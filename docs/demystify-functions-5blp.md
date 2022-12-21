# 揭开函数的神秘面纱

> 原文：<https://dev.to/stereobooster/demystify-functions-5blp>

在我之前的一篇文章中，我谈到了函数的理论观点。在这篇文章中，我们将讨论如何用编程语言从头开始实现函数。

这篇文章是这个系列的一部分:在以前的文章中，我们构建了小型语言，现在可以做`+`、`-`、`define`(全局范围变量)。在这个函数中，我们将添加`function`操作，它将创建一个新函数。我们将向现有类型(`symbol`、`number`)的列表中添加一个新类型(`function`)。

## 我们将覆盖什么？

这是学习练习，这意味着我们将只实现有限的功能，例如，我们将使用动态变量解析而不是词法范围，我们不会谈论递归或堆栈溢出错误或尾部调用优化，我们还不会支持闭包(这是下一篇文章)，评估策略(大多数时间我们将使用按值调用)。

我们将实现这样一个功能:

```
> (define minus
    (function (x y)
      (- x y)))
> (minus 2 1)
= 1 
```

例如，`(function ...)`返回一个我们赋给变量(`minus`)的函数，稍后我们可以像调用内置函数一样调用它。

## 实现

创建一个函数需要什么？我们需要三样东西

*   作为这是表达式的信号的关键字`function`是函数声明。其他的 Lisp 风格可能会用`lambda`、`λ`或者`\`来代替。
*   函数参数列表
*   函数体

例如:

```
;                 function body⤵
(define minus (function (x y) (- x y)))
;              arguments⤴ 
```

函数调用将使用一个环境来评估主体，该环境将具有以与参数相同的方式命名的变量，例如

```
(minus 2 1) 
```

与
相同

```
evaluate(parse(`(- x y)`), { x: 2, y: 1 }); 
```

**函数是带有一些局部变量的子程序(或例程)**。

### 函数为数值

函数是一个值，所以我们可以把它赋给变量:

```
(define minus (function (x y) (- x y))) 
```

如果我们可以将它赋给一个变量，这意味着我们需要以某种可存储在内存中的方式来表示一个函数。我们将如何做？

我们可以将它存储为列表:

*   首先将是关键字“功能”(标签)
*   第二个是参数列表
*   第三个是函数体

百米...似乎很熟悉🤔。我们可以重用函数的 AST 作为函数表示

```
const evaluate = (ast, environment = {}) => {
  // ...
  // function call handling
  let [name, first, second] = ast;
  const numberOfArguments = ast.length - 1;
  if (name === "+") {
    // ...
  } else if (name === "function") {
    return ast;
  } else {
    // ...
  }
}; 
```

我们可以这样检测函数:

```
const isFunction = ast => isList(ast) && ast[0] === "function"; 
```

### 函数调用

让我们添加对函数调用的支持。正如我们之前讨论过的，函数调用只是用附加的局部变量来求值:

```
const evaluate = (ast, environment = {}) => {
  // ...
  if (name === "+") {
    return evaluate(first, environment) + evaluate(second, environment);
    //...
  } else {
    if (!isFunction(environment[name])) {
      throw new RuntimeError(`"${name}" is not a function`);
    }
    // take function and destructure it to arguments and body
    const [_, argumentNames, body] = environment[name];
    // assume all functions expect 2 arguments
    const functionEnvironment = {
      // take current environment
      ...environment,
      // add arguments to environment
      [argumentNames[0]]: evaluate(first, environment),
      [argumentNames[1]]: evaluate(second, environment)
    };
    // pass body and new environment to evaluate
    return evaluate(body, functionEnvironment);
  }
}; 
```

就是这样。我们实现了函数。现在来说说细节。

### 局部变量

为什么他们称之为局部变量？局部变量和全局变量的区别在于全局变量在任何地方都是可访问的(一旦定义)，但是局部变量只在函数内部可用。

例如:

```
> (define z 1)
= 1
> (+ z z)
= 2 
```

它将返回到 2。

```
(define minus (function (x y) (- x y))) 
```

正如你所看到的，我们使用了`x`和`y`变量，这意味着它们是被定义的(至少在函数内部)。现在如果我们尝试

```
> (minus 2 1)
= 1
> (+ x y) 
```

它会抛出一个关于未定义变量`x`和`y`的异常，因为它们并不全局存在。

每个函数都有它的作用域，但它包含了全局作用域中的所有变量。

### 可变遮蔽

让我们看更多的例子:

```
> (define z 1)
= 1
> (define minuzzz (function (x y) (- (- x y) z)))
> (minuzzz 2 1)
= 0 
```

我们可以看到`minuzzz`函数已经访问了全局作用域(`z`变量)。这很有道理，但是这个例子怎么样

```
> (define x 1)
= 1
> (define minus (function (x y) (- x y)))
> (minus 2 1)
= 1 
```

`x`存在于全球和本地。在这种情况下，局部版本“获胜”，这被称为变量阴影(局部变量阴影全局一)。

### 动态分辨率

如果我们做了会发生什么:

```
> (define getFun
        (function (x y)
          (function (i j)
            (- (+ x y) (+ i j))
          )
        )
      )
> (define fun (getFun 5 4))
> (fun 3 2) 
```

`getFun`是返回函数的函数。我们给`fun`分配一个由`getFun`返回的函数(将`x`和`y`分别替换为 5 和 4)。

我希望`(fun 3 2)`扩展到下面的表达式`(- (+ 5 4) (+ 3 2))`或算术符号`((5 + 4) - (3 + 2))`，并计算为`4`。但是，这反而会导致错误`Can't find "y" variable...`。这是因为我们使用“动态”解析，我们不保留环境，只有一个全局环境和一个函数环境，但是为了支持这种情况，我们需要在创建时保存每个函数的环境，并将其与函数一起传递。这个函数与一个叫做 closure 的环境一起传递，我们将在下一篇文章中实现 closure。

### 原生函数

现在我们可以用自己的语言定义函数了，我们看到了`+`和`-`之间的一些区别，比如，和用户定义的函数。

`+`和`-`使用“本地”功能，例如底层平台的能力来执行实际操作。如果我们使用汇编语言而不是 JS，它可能是一些特定于处理器的指令，例如:

三操作数架构(RISC - PowerPC)

```
;A:= B+C
lwz r2, [num1]
lwz r3, [num2]
add r4,r3,r2 
```

双操作数体系结构(CISC - x86)

```
;A:=B
mov eax, [num1]
mov ebx, [num2]
;A:=A+B
add eax,ebx 
```

[汇编片段的来源](https://www.quora.com/How-do-I-add-two-numbers-in-assembly-language/answer/Alexandre-Horst)。

### 环境中的功能

现在，当我们可以在环境中存储用户创建的函数时，我们也可以考虑在环境中存储一些内置函数，这样我们可以稍微简化代码。

我们可以将`+`、`-`函数移到环境中，但不能将`define`和`function`函数移到环境中。(想想我们为什么不能。)

通过这样做，我们将能够删除一些代码:

```
const evaluate = (ast, environment = {}) => {
  // ...
  // function call handling
  let [name, first, second] = ast;
  const numberOfArguments = ast.length - 1;
- if (name === "+") {
-   return evaluate(first, environment) + evaluate(second, environment);
- } else if (name === "-") {
-   return evaluate(first, environment) - evaluate(second, environment);
- } else if (name === "define") { + if (name === "define") {
    // ...
    if (
      environment[first] !== undefined ||
-     first === "+" ||
-     first === "-" ||
      first === "define" ||
      first === "function"
    ) {
      throw new RuntimeError(`Can't redefine "${first}" variable`);
    }
    // ...
  }
}; 
```

将函数移动到环境:

```
const defaultEnvironment = {
  "+": (a, b) => a + b,
  "-": (a, b) => a - b
};

const evaluate = (ast, environment = { ...defaultEnvironment }) => { 
```

添加处理函数调用的逻辑:

```
const evaluate = (ast, environment = { ...defaultEnvironment }) => {
  // ...
  if (name === "define") {
    // ...
  } else {
    if (isNativeFunction(environment[name])) {
      return environment[name](
        evaluate(first, environment),
        evaluate(second, environment)
      );
    }
    if (isFunction(environment[name])) {
      // ...
    }
  }
}; 
```

## PS

这只是函数的开始。我们仍然需要涵盖很多主题，但基本的想法已经到位。

这篇文章的源代码是[这里](https://github.com/stereobooster/write-a-language/tree/master/4.function)和[这里](https://github.com/stereobooster/write-a-language/tree/master/5.functions-in-environment)。