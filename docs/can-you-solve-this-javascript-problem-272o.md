# 你能解决这个 JavaScript 问题吗？

> 原文：<https://dev.to/varundey/can-you-solve-this-javascript-problem-272o>

> 你也可以在我的网站上找到这篇文章的副本

我最近偶然发现了这个 JavaScript 脑筋急转弯，我想和大家分享一下。

> 创建一个函数，它接受一组函数作为参数，并对它们执行从左到右的组合。然后，它从一个函数返回结果，该函数接受一个参数，并对该参数执行合成。

### 举例:

```
const addOne = num => num + 1;
const substractTwo = num => num - 2;
const multiplyThree = num => num * 3;

const resp = compose(addOne, substractTwo, multiplyThree);
const result = resp(4);
console.log(result);    // 9

/**
This is similar to multiplyThree(substractTwo(addOne(4)));
*/ 
```

好玩吧？我花了大约 20 分钟想出了一个没有谷歌/配对编码的工作解决方案。我使用经典的普通 JavaScript，浏览器控制台作为我的编辑器，console.logs/break 点用于调试。😅我当然希望你能做得更好。在进一步阅读之前，我建议您提出自己的工作实现。

## 剧透警报

从这一节开始，我将写下解决这个问题方法。这是我如何解决它的演练。这将是一个很好的点，以编写自己的解决方案之前，通过这些步骤。如果你被困在某个地方，你可以从下面的列表跳到那个部分(假设你的方法和我的一样)。我想你已经被警告过了吧？🤷‍♂️

### 识别问题陈述的部分

到目前为止，通过仔细研究这个问题，我知道。我需要创建一个函数
2。这个函数应该带一堆函数参数
3。应该返回一个函数
4。这个返回函数应该取输入值
5。进行计算
6。返回结果

因为对于原型，我发现在 Chrome 开发工具中创建一个代码片段是最容易的。我打开 Chrome 浏览器，在`Sources`标签的`Snippets`部分创建了一个片段`composition.js`。我通常走这条路，因为它帮助我设置 console.logs 并放置断点，而不需要创建不必要的 web 应用程序。

### 1。创建函数

这可能是最简单的一步。作为这一步的一部分，我还将设置给定的示例参数

```
const addOne = num => num + 1;
const substractTwo = num => num - 2;
const multiplyThree = num => num * 3;

const compose = () => {} 
```

### 2。未知数量的参数

现在我已经有了我的虚拟函数，我需要传入未知数量的参数。这很简单。在 JavaScript 函数中唯一可以传入未知数量参数的方法是`...args`。这将返回一个传递的参数数组。

```
const compose = (...args) => console.log(args);

compose(1, 2, 3); 
```

### 3。返回一个函数

到目前为止，我已经建立了一个函数，它接受一堆参数并打印出来。它一直工作到现在。现在从给出的例子来看，很明显，最终结果存在于另一个函数闭包中，这个闭包似乎是从`compose`函数返回的。

```
const compose = (...funcs) => {
    return () => console.log(funcs)
}

const result = compose(addOne, substractTwo, multiplyThree);
result(); 
```

### 4。使闭包接受输入

现在我已经创建了我的闭包，我需要让它接受一个论点，我将验证它在这一点上是正确的。

```
const compose = (...funcs) => {
    return n => console.log(funcs, n)
}

const result = compose(addOne, substractTwo, multiplyThree);
result(4); 
```

### 5。做计算

这是我花了大部分时间的步骤。如果你没有看上面的任何步骤就走到了这里，那么恭喜你！我仍然建议在进一步阅读之前尽力而为。

现在我所有的函数都工作正常，我需要在某个地方进行计算。但是在哪里？它应该放在构造函数里面吗？还是应该驻留在闭包里？🤔*想凡荣，想。*

仔细看看这个例子。`compose`接受函数参数，但如果没有输入数字，它们就没有任何意义。结论就是我们讨论的地方。所以计算应该是闭包函数的一部分。

酷毙了。但是我该怎么做呢？

嗯..因为我们是从左到右组合函数，所以我需要将输入传递给第一个函数。其结果应该作为参数传递给第二个函数，以此类推。

但是我该怎么做呢？

看起来我已经有了数组列表的函数，因为我不需要改变数组的元素，所以我可以使用一个`forEach`。

#### 迭代 1 次

```
const compose = (...funcs) => {
    return n => funcs.forEach(func => console.log(func))
} 
```

#### 迭代 2 次

```
const compose = (...funcs) => {
    return n => funcs.forEach(func => console.log(func(n)))
} 
```

现在到了棘手的部分。我需要将函数的结果作为参数传递给另一个函数。我将利用闭包具有其父函数的作用域这一事实。

#### 迭代 3 次

```
const compose = (...funcs) => {
    return n => {
        let result;
        funcs.forEach(func => {
            result = func(n);
        })
    }
} 
```

我在`forEach`里面设置了一个断点，意识到了自己的错误。这样不行。这将接受每个函数参数的相同输入，并将把`result`赋给该函数的返回值。我需要把它作为第一个参数的输入，以及其余参数的结果。

嗯。这似乎是一个简单的 if/else 条件。但是要做到这一点，我还需要为循环建立索引。咩。我可能可以用更多的 JavaScript 方式来做这件事。

#### 迭代 4 次

```
const compose = (...funcs) => {
    return n => {
        let result;
        funcs.forEach(func => {
            result = func(result || n);
        });
    }
} 
```

从我在早期迭代中设置的断点，我可以看到它正在按预期工作。但是记住，如果你把操作符换成 or 条件，这是行不通的。因为我们需要短路 OR，所以我们需要在输入之前检查结果是否存在。如果我们交换操作符，`n`将总是出现在`result`之前，我们将回到迭代 3。

### 6。返回结果

我们已经将答案存储在`result`变量中。我们只需要把它还给呼叫者。如果你已经到达这里，这应该很容易，

```
const compose = (...funcs) => {
    return n => {
        let result;
        funcs.forEach(func => {
            result = func(result || n);
        });
        return result;
    }
} 
```

我们结束了。我最终的解决方案是去掉多余的括号，让它对 ES8 更友好，就像这样。

```
const compose = (...funcs) => n => {
    let result;
    funcs.forEach(func => result = func(result || n));
    return result;
}

const addOne = num => num + 1;
const substractTwo = num => num - 2;
const multiplyThree = num => num * 3;

const res = compose(addOne, substractTwo, multiplyThree);
res(4);     // 9

// We can also curry it together
compose(addOne, substractTwo, multiplyThree)(5);    // 12 
```

就是这样。这个例子很好地测试了您的 JavaScript 闭包和 currying 技巧。我相当肯定你也可以用`.reduce()`来做这件事，但是我总是倾向于忘记 reduce 的论点是如何工作的，因为我挑战自己不要打开 Google，所以我想到了这个。请在评论中告诉我你做得有多好。✌️