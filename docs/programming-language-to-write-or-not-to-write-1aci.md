# 揭开编程语言的神秘面纱

> 原文：<https://dev.to/stereobooster/programming-language-to-write-or-not-to-write-1aci>

编程语言(PL)被视为一种宗教。人们围绕着 PL 有神圣的战争。人们混淆了范式和语言。

> 任何足够先进的技术都和魔法没什么区别。
> 
> -克拉克第三定律

你可能想写一个编程语言来揭开它的神秘面纱。编程语言只是一种工具。

## 学习锻炼

不要把它想成是你在工作中使用的语言，或者是生产中会用到的东西，而是把它当成一次学习经历。主要的收获是理解编程语言背后的逻辑，而不是编写高性能或详尽的实现。

这项工作遵循两个原则:

*   [白手起家](https://stereobooster.com/posts/about-learning/#building-from-scratch)
*   [“问题优先”方法](https://stereobooster.com/posts/about-learning/#problem-first-approach)

## 什么？

我们要写什么样的语言？口齿伶俐。等等，不要关闭浏览器。听我说完。我可以解释为什么。

正如我所说的，这是学习练习，我们希望专注于编程语言本身的逻辑，我们希望尽可能地消除复杂性。我们不想在分词器、词法分析器、解析器、编译器等上面浪费时间。我们想深入核心。Lisp 非常适合这个目的，因为它几乎没有语法，这意味着为它实现一个解析器非常容易。

解析器最简单的实现只有一种解析错误——没有匹配的括号。

### 但是括号

不需要用 Lisp 写很长的程序。我们将实现它的最小子集。所以括号的数量是可以接受的。

不要忘记括号的选择是任意的:

```
// Lisp
(a b)
// C-like
a(b)
// Ruby
c.a b
c.a(b)
c.send(:a, b)
// Lua
c.a(c, b)
c:a(b) 
```

## 如何？

我们将实现尽可能少的类似 Lisp 的语言，并根据需要扩展它。我们将用 JavaScript 实现它。为什么？因为如果你用网络浏览器阅读这篇文章，这意味着你的机器上已经有 JS 了。

### 没有装配？没有编译器？

有些人可能会对我们在另一个 PL 中实现一个 PL 感到困惑。不是出轨吗？不应该做编译器吗？还是用汇编？

这里的技巧是，如果你可以用图灵完整语言实现某个东西，你就可以(理论上)移植到任何其他图灵机上(这是因为你可以在另一个图灵机中实现一个图灵机——一路向下)。

用一个 PL 实现另一个 PL 是可以的。

## 让我们试试吧

这个帖子的灵感来源于[(如何用 Python 写一个(Lisp)解释器)](https://norvig.com/lispy.html)。原帖挺好的，可以看看那个。我的解释和原解释的主要区别是我如何划分材料。我这样做是为了清楚地展示向语言中添加每个新特性需要做些什么。

作为第一步，我们将实现计算器语言。它将提供`+`、`-`运算和数值。看起来不多，但是我们会学到 REPL、标记化、解析、AST 和评估。

### 程序如何执行？

编程语言运行时(又名解释器)执行以下步骤:

1.  读取程序的文本，例如，从文件系统或其他输入中读取
2.  解析文本——将文本转换为内部表示形式，然后进行计算
3.  评估(执行)指令

### 评价

计算器语言的求值与计算是一样的，但对于更复杂的语言求值也意味着它将使计算机做其他事情，如从输入中读取、打印到输出、发出声音、使灯闪烁等。

例如，`5 - (2 + 1)`评估为`2`。作为第一步，我们需要评估`(2 + 1)`到`3`，然后再评估`5 - 3`到`2`。

这个例子是一个小程序。该程序由小指令(步骤)组成，计算机可以逐个或并行评估这些指令。为了简单起见，我们将假设指令被一个接一个地执行。

程序文本中的指令并不总是按照它们在程序中出现的顺序执行，例如`-`在`+`之前，但是它在第二个执行。

> 句法-规定计算机语言中单词和短语必须如何使用的规则。
> 
> [牛津学习词典](https://www.oxfordlearnersdictionaries.com/definition/english/syntax)

执行顺序由语法决定。当一种语言有流控制指令时，它的工作方式会有所不同，但是我们还没有。在我们的例子中，执行顺序完全由语法规则决定。

执行的顺序很重要，因为`5 - (2 + 1)`是`2`，但是`5 - 2 + 1`是`4`。

### Lisp 语法

这是标准的算术符号:`5 - (2 + 1)`。Lisp 中同样的例子会是这样的:`(- 5 (+ 2 1))`。

首先，这可能会让你感到困惑，但让我们看看如何从一个转换到另一个:

1.  加括号(不改变意思):`5 - (2 + 1)`——>——T1。
2.  由中缀符号改为前缀符号:`(5 - (2 + 1))`->-T1】

中缀符号-当函数名(`+`，`-`)；也可以称为操作)位于函数的自变量之间(也可以称为操作数)，例如`a + b`。

前缀符号——当函数名位于参数之前时，例如，`+ a b`。

这个语法有一些扩展，但是我们不需要它们用于计算器。

### 解析

解析是将文本转换为内部表示(即所谓语法树)的过程。

树是数据结构。语法树意味着它是根据语法规则建立的。

数据结构是我们(开发人员)在计算机内部组织数据的一种方式。例如:

*   单一值。珍的出生年份是`2000`
*   列表。我的队友的出生年份是`2000, 2001, 2002`
*   记录。我的队友的出生年份是`Jen: 2000, Ben: 2001, Ken: 2002`

树是组织分层数据的一种方式。例如，文件系统(没有链接)是一棵树

```
home
 ├ My documents
 │ └ Picture.jpg
 ├ My music
 └ My videos 
```

可以用嵌套列表(列表中的列表)来实现树。JavaScript 中的数组是一种表示列表的方式(不是链表，而是一般意义上的列表的概念)。

```
const list = [2000, 2001, 2002];
const tree = [
  "home",
  [["My documents", ["Picture.jpg"]], "My music", "My videos"]
]; 
```

> 树是由有向边连接的节点的集合。
> 
> *   一个节点被区分为根；
> *   每个节点(除了根之外)都由来自恰好一个其它节点有向边连接；一个方向是:父->子
> 
> -[15-111 中高级编程在线教材](http://www.cs.cmu.edu/~clo/www/CMU/DataStructures/Lessons/lesson4_1.htm)

通过解析下面的程序

```
(- 5
 (+ 2 1)) 
```

我们将得到下面的(抽象的)语法树:

```
["-", 5, ["+", 2, 1]]; 
```

语法树有两种风格:抽象的和具体的。在 AST(抽象语法树)中，我们删除不改变程序含义的细节，例如，空白和新行，但在 CST 中，这些信息被保留下来。当您想要操作源代码但保留格式时，您可能需要 CST，例如，在 IDE 中进行“重构”，如重命名变量。

### 标记化

标记化可以是解析的子步骤之一。记号化是将程序文本转换成记号列表(单词和标点符号)的方法。然后解析器可以从列表(或流)中读取标记，并从中创建 AST。

tokenistation 将转换

```
(- 5 (+ 2 1)) 
```

至

```
["(", "-", "5", "(", "+", "2", "1", ")", ")"]; 
```

这不是必需的，但是这个子步骤会使解析变得更容易一些。

### 实现解析器

令牌化器的简单(非最佳)实现:

*   获取文本(JS 中的字符串)
*   将所有括号(`(`、`)`)替换为由空格(`(`、`)`)包围的括号
*   用一个空格替换任意数量的后续类空格字符(制表符、空格、换行符)
*   按空间分割

```
// Convert a string of characters into a list of tokens.
const tokenize = program =>
  program
    .replace(/\(/g, " ( ")
    .replace(/\)/g, " ) ")
    .replace(/^\s+|\s+$/g, "")
    .split(/\s+/g); 
```

测试它:

```
const assert = require("assert");
const program = "(- 5 (+ 2 1))";
assert.deepStrictEqual(tokenize(program), [
  "(",
  "-",
  "5",
  "(",
  "+",
  "2",
  "1",
  ")",
  ")"
]); 
```

解析器的简单(非最佳)实现:

*   `tokens_to_ast`常规
*   拿一张代币清单
*   从列表中选择第一个(`shift`)
*   检查是否是`(`，如果是
*   开始一个新的列表(JS 情况下的数组，`let L = [];`)
*   用剩余的代币打电话给`tokens_to_ast`
*   将(`push`)结果放入新创建的列表(`L`)中
*   重复直到到达`)`
*   作为例程执行结果的返回列表(`L`)
*   如果不是`(`
*   检查是否是`)`，这是一个错误程序不能用`)`启动
*   检查是否是号码`if (!isNaN(parseFloat(token))) {`
*   如果是，返回号码
*   否则，返回一个字符串(字符串是一段文本)。在 Lisp 中，他们称之为符号或原子，但在 JS 中我们将使用字符串。

```
const parse = program => tokens_to_ast(tokenize(program));

const tokens_to_ast = tokens => {
  if (tokens.length === 0) {
    throw new SyntaxError("Can't parse empty program");
  }
  const token = tokens.shift();
  if (token === "(") {
    let L = [];
    while (tokens[0] !== ")") {
      L.push(tokens_to_ast(tokens));
    }
    tokens.shift(); // pop off ')'
    return L;
  } else if (token === ")") {
    throw new SyntaxError("Unexpected closing parenthesis");
  } else if (!isNaN(parseFloat(token))) {
    // Numbers become numbers
    return parseFloat(token);
  } else {
    // every other token is a symbol or an atom
    // for simplicity we use strings
    return token;
  }
}; 
```

解析器测试

```
assert.deepStrictEqual(parse(program), ["-", 5, ["+", 2, 1]]); 
```

### 实现评价者

让我们想想评估以下程序需要什么:`(+ 2 2)`和`(- 2 2)`。我们需要取 AST，在函数名，第一个和第二个参数中析构它，然后根据函数名进行计算:

```
const evaluate = ast => {
  // function call handling
  let [name, first, second] = ast;
  if (name === "+") {
    return first + second;
  } else if (name === "-") {
    return first - second;
  } else {
    // runtime error
    throw new Error(`${name} is not a function`);
  }
}; 
```

但是该评估器不能处理以下情况:`(+ 2 (+ 2 2))`。另一方面，我们可以处理嵌套表达式，例如`(+ 2 2)`，所以也许我们可以在赋值器中使用赋值器🤔。

```
const evaluate = ast => {
  // number handling, like this: 2
  if (typeof ast === "number") {
    return ast;
  } else {
    // function call handling
    let [name, first, second] = ast;
    if (name === "+") {
      return evaluate(first) + evaluate(second);
    } else if (name === "-") {
      return evaluate(first) - evaluate(second);
    } else {
      // runtime error
      throw new Error(`${name} is not a function`);
    }
  }
}; 
```

这是它-我们有计算器语言的评估工作。这不是一段非常通用的代码，但是实现起来非常简单。一旦我们想要添加更多的功能，我们就需要更改代码，但这是练习的一部分，我们将了解添加新功能需要做什么样的更改。

评估员测试:

```
assert.deepStrictEqual(evaluate(["-", 5, ["+", 2, 1]]), 2); 
```

## REPL

我们已经有了语言的核心，让我们添加一些能够与之交互的接口。REPL 代表:

*   read——读取用户通过界面提供的程序文本
*   Eval -评估计划
*   打印-打印结果
*   循环-从头开始重复这个过程

REPL 是一个简单的编程语言解释器的交互界面。目前，我们的语言既没有 read，也没有 write，也没有 loop 函数，所以我们将在核心之外实现这种交互(用 JS)。我们可以通过两种方式实现:网页或者 Node.js 命令行界面(CLI)。

### 网页中的 REPL

让我们试试网页。我们将从 HTML 文本字段中读取用户输入，在表单 submit 上对其进行评估，并将结果打印到 textarea。

```
<html>
  <body>
    <form id="form">
      <textarea id="program" placeholder="program"></textarea><br /><br />
      <input type="submit" value="evaluate" /><br /><br />
      <textarea id="result" placeholder="result"></textarea>
    </form>
    <script>
      // implementation of parse and evaluate functions which we wrote before
      // ...
      const form = document.getElementById("form");
      const programInput = document.getElementById("program");
      const resultOutput = document.getElementById("result");
      form.addEventListener("submit", e => {
        // prevent page reload
        e.preventDefault();
        try {
          // evaluate a program
          const result = evaluate(parse(programInput.value));
          // and print it to the textarea
          resultOutput.value = result;
        } catch (e) {
          // in case of error print the error to the textarea
          resultOutput.value = e.message;
        }
      });
    </script>
  </body>
</html> 
```

### CLI 中的 REPL

```
// implementation of parse and evaluate functions which we wrote before
// ...
const readline = require("readline");
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
  prompt: "calcy> "
});
rl.prompt();

rl.on("line", input => {
  try {
    console.log(evaluate(parse(input)));
  } catch (e) {
    console.log(e.message);
  }
  rl.prompt();
}); 
```

## 结论

在本教程中，我们为将来的学习打下了基础。例如，下一个任务可以是向语言中添加变量(一种保存计算结果的方法，以便能够在不同的任务中重用它)，或者添加函数，或者添加对函数中更大或更小数量的参数的处理(目前所有函数都只接受两个参数)。这么多学习机会。

我猜在下一个教程中我们会添加变量、[函数和闭包](https://stereobooster.com/posts/from-function-to-closure)。

源代码这里是[这里是](https://github.com/stereobooster/write-a-language/tree/master/1.calcy)。

> 马修·施瓦茨在 unsplash 上拍摄的照片