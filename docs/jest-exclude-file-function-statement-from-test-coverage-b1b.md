# Jest 从测试覆盖中排除文件/函数/语句

> 原文：<https://dev.to/hugo__df/jest-exclude-file-function-statement-from-test-coverage-b1b>

> 在计算机科学中，测试覆盖率是一种度量，用于描述在特定测试套件运行时程序源代码的执行程度。
> 
> [代码覆盖率-维基百科](https://en.wikipedia.org/wiki/Code_coverage)

代码覆盖率通常被用作软件的质量度量，例如“我们的代码必须有 80%以上的测试覆盖率”。用 Jest 收集测试覆盖率就像在调用时使用`--coverage`标志一样简单。

这篇文章讲述了如何使用配置或伊斯坦布尔杂注忽略 Jest 中的文件、函数和语句。以及你为什么/如何做这样的事情的原因和限制。

你可以在 github.com/HugoDF/jest-ignore-coverage 找到一个工作范例库。

## Jest 连覆盖率怎么算？

Jest 使用[伊斯坦布尔](https://github.com/istanbuljs/istanbuljs)来计算覆盖率。Jest 通常从最终用户那里抽象出这一点，您在应用程序中所要做的就是调用`jest --coverage`(并配置适当的覆盖配置字段)。伊斯坦布尔在内部使用的事实表明，例如，报道记者的[文档提到“任何](https://jestjs.io/docs/en/configuration.html#coveragereporters-array-string)[伊斯坦布尔记者](https://github.com/istanbuljs/istanbuljs/tree/master/packages/istanbul-reports/lib)都可以使用。”，它显示了实际收集覆盖数据和生成报告的内容。

## 为什么我要将文件排除在覆盖范围之外？

正如伊斯坦布尔报道图书馆的维护者和作者所说:

> JS 代码中的一些分支通常很难测试，如果不是不可能的话。例如 hasOwnProperty 检查、UMD 包装器等等。伊斯坦布尔现在有一个设施，通过它可以排除某些代码段的覆盖。
> 
> [伊斯坦布尔-出于覆盖目的忽略代码](https://github.com/gotwarlost/istanbul/blob/master/ignoring-code-for-coverage.md#ignoring-code-for-coverage-purposes)

此外，在大多数情况下，100%的覆盖率是不必要的，甚至是不合理的。有些文件不包含任何(业务)逻辑。或者它们包含以非常明显的方式失败的逻辑(例如，启动器在启动时崩溃)。

例如，引导应用程序的脚本可能会绑定到一个端口，这使得测试变得不方便。导入所有不同依赖项并在 Express 设置中`app.use()` -es 它们的文件可能是避免单元测试/依赖模仿地狱的另一个候选文件。

出于覆盖率的目的，您可能想要忽略的另一类文件/函数是特定于测试的助手。它们中的一些不作为测试的一部分运行也没关系，因为它们不是被测试的代码。

正如软件中的许多事情一样，这是关于权衡的。

## 通过不使用配置运行相关测试，将文件从 Jest 覆盖范围中排除

有一个 Jest 配置选项`testPathIgnorePatterns` ( [参见 testPathIgnorePatterns](https://jestjs.io/docs/en/configuration.html#testpathignorepatterns-array-string) 的文档)

最简单的配置方法是通过`package.json` :

```
{  "jest":  {  "testPathIgnorePatterns"  :  [  "<rootDir>/ignore/this/path/"  ]  }  } 
```

在[使用 GitHub](https://github.com/HugoDF/jest-ignore-coverage#exclude-files-from-jest-coverage-using-configuration) 上的配置从 Jest 覆盖中排除文件。

## 通过不将文件包括在覆盖范围集合配置中，从覆盖范围中排除文件

作为不运行测试(参见“通过不使用配置运行相关测试从 Jest 覆盖中排除文件”)的替代或补充，通过不将其包括在覆盖报告中，这由`collectCoverageFrom` Jest 配置选项控制([参见来自](https://jestjs.io/docs/en/configuration.html#collectcoveragefrom-array)的 Jest collectCoverageFrom 的文档)。

使用类似下面的内容:

```
{  "jest":  {  "collectCoverageFrom":  [  "src/**/{!(ignore-me),}.js"  ]  }  } 
```

**重要的**:一定要用`()`把被忽略的文件名括起来。

在[使用 GitHub](https://github.com/HugoDF/jest-ignore-coverage#exclude-files-from-jest-coverage-using-configuration) 上的配置从 Jest 覆盖中排除文件。

## 从文件级 Jest 覆盖中排除文件

我们可以在任何文件的顶部使用下面的注释来使用伊斯坦布尔杂注来忽略文件:

```
/* istanbul ignore file */ 
```

在 GitHub 上的文件级从 Jest 报道中排除文件

## 从 Jest 覆盖中排除功能

```
/* istanbul ignore next */
function myFunc() {
  console.log(
    "Not covered but won't appear on coverage reports as such"
  );
} 
```

从 GitHub 上的 Jest 报道中排除函数或语句。

## 从 Jest 报道中排除陈述

如果可以的话，避免这种情况，如果你正在测试一些代码，你可能应该测试所有代码的***。*** 

```
function myFunc(a) {
  /* istanbul ignore else */
  if (a) {
    // do some work
  } else {
    // do some other work
  }
} 
```

从 GitHub 上的 Jest 报道中排除函数或语句。

## 进一步阅读

参见[关于忽略代码覆盖率的原始伊斯坦布尔文档](https://github.com/gotwarlost/istanbul/blob/master/ignoring-code-for-coverage.md)以更广泛地了解如何在不同情况下做到这一点。

我还整理了一份案例报告，包括所有不同的案例[github.com/HugoDF/jest-ignore-coverage](https://github.com/HugoDF/jest-ignore-coverage)。

查尔斯🇵🇭*