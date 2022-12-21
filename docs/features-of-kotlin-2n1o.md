# 科特林的特色

> 原文：<https://dev.to/jay_tillu/features-of-kotlin-2n1o>

Kotlin 为您提供了一些超越 Java 的惊人而强大的特性。这也是开发者热爱 Kotlin 的原因。在谷歌宣布官方支持 Kotlin 之前，有许多科技巨头都在使用它。

以下是 Kotlin 的七个主要特征:

1.  简明代码
2.  零安全
3.  表达代码
4.  现代特征
5.  与 Java 的互操作性
6.  javascript 蒸腾
7.  原生转换(科特林原生)

## 简明代码

* * *

开发人员总是喜欢干净简洁的代码。更少的代码需要更少的时间来编写，更少的时间来阅读，也使维护它变得容易。

与 java 相比，Kotlin 代码非常简洁。它极大地减少了样板代码的数量。因此，与 java 相比，你用 Kotlin 编写的代码量更少，这提高了你的开发速度。

粗略估计表明，与 java 相比，Kotlin 需要少 40%的代码行。

## 空安全

* * *

超过 70%的 android 应用由于 java 的空指针异常而崩溃。Java 并没有提供任何防止空值的方法。开发者必须自己处理它。

但是 Kotlin 很好地处理了空值。在 Kotlin 中，你不能隐式地得到空指针异常。默认情况下，Kotlin 编译器不允许任何类型在编译时有 null 值。因此，如果你使用 Kotlin，那么它将减少你的应用程序崩溃，并为你的用户提供更好的用户体验。

## 富有表现力的代码

* * *

表达性代码是指每个程序员都能容易理解的代码。

科特林真的很有表现力。所有数据类型、内置函数、关键字等。非常有表现力并且容易理解。Kotlin 的设计是这样的，即使一个从来没有用 kotlin 编写代码的人也可以很容易地理解它的代码。

## 现代特征

* * *

由于 kotlin 是第四代语言，它引入并结合了许多新特性，如 Lambda 函数、智能强制转换、空安全、运算符重载等。这将有助于你提高工作效率。科特林受到六种主要语言的影响，并继承了它们的许多优点。

## 与 java 的互通性

* * *

Kotlin 与 Java 100%互操作。你可以很容易地从 Java 调用 Kotlin 代码，从 Kotlin 调用 Java 代码。这使得采用更容易，风险更低。IDE 中还有一个自动化的 Java-to-Kotlin 转换器，可以简化现有代码的移植。这使得在现有的 Android 项目上工作变得容易。您可以保持旧的 java 文件不变，并在新的 kotlin 文件中创建新的特性。

## JavaScript 翻译

* * *

您可以将 kotlin 代码转换为 JavaScript 代码。这样，即使你的 kotlin 代码也可以在浏览器上运行。当您选择 JavaScript 目标时，作为项目一部分的任何 Kotlin 代码以及 Kotlin 附带的标准库都被转换成 JavaScript。然而，这不包括 JDK 和任何使用的 JVM 或 Java 框架或库。任何不是 Kotlin 的文件在编译时都会被忽略。

根据官方文档，当前的实现目标是 ECMAScript 5.1，但也有计划最终目标是 ECMAScript 2015。

Kotlin 编译器试图符合以下目标:

*   提供最佳大小的输出
*   提供可读的 JavaScript 输出
*   提供与现有模块系统的互操作性
*   无论是针对 JavaScript 还是 JVM，都要在标准库中提供相同的功能(尽最大可能)。

## 原生转换(Kotlin Native) (Beta)

* * *

[![](img/752bbdd6e2e4d7523283bf172d7dc6e4.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--76Td0d13--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://kotlinlang.org/asseimg/landing/native/native_overview.png) 
Kotlin Native 是一种将 Kotlin 代码编译成原生二进制的技术，可以在没有虚拟机的情况下运行。这样，你的 kotlin 代码将直接在一个系统上运行，而不需要任何额外的运行时或虚拟机。

请注意，kotlin native 仍处于测试阶段(截至 2019 年 7 月 12 日)

**目标平台**
Kotlin 原生支持以下平台:

*   iOS (arm32、arm64、仿真器 x86_64)
*   MacOS (x86_64)
*   安卓系统(arm32，arm64)
*   Windows (mingw x86_64)
*   Linux (x86_64、arm32、MIPS、MIPS 小端)
*   WebAssembly (wasm32)

所以上面的人是科特林的主要特征。如果我错过了你最喜欢的，请在评论中告诉我。

请每天查看关于 Kotlin 和其他编程主题的新帖子。在那之前，继续编码，继续爱。

> 想和我联系吗？以下是链接。我很乐意成为你的朋友。😊
> [Twitter](https://twitter.com/jay_tillu)
> [脸书](https://www.facebook.com/jaytillu.1314/)
> [insta gram](https://www.instagram.com/jay.tillu/)
> [Medium](https://medium.com/jay-tillu)
> 或者直接发邮件给我[jayviveki13@gmail.com](mailto:jayviveki13@gmail.com)