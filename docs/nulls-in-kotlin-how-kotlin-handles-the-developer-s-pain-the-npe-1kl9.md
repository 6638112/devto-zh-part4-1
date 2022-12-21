# 科特林的 Nulls。科特林如何处理开发者之痛“NPE”

> 原文：<https://dev.to/jay_tillu/nulls-in-kotlin-how-kotlin-handles-the-developer-s-pain-the-npe-1kl9>

如果你问任何一个 android 或 java 开发者关于最可怕的异常，他/她只会说一个名字，那就是 NPE 或空指针异常。由于空指针异常，超过 70%的应用程序在其生命周期内崩溃。空指针是 android 和 java 开发人员最痛苦的例外之一。

这就是为什么当 JetBrains 团队设计 kotlin 时，他们相当重视处理 null，并提出了一个神奇的解决方案，它确实非常有效地提供了针对 null 的安全性。让我们看看 kotlin 处理空值有多漂亮。

## 什么是 null 和 null 指针异常？

* * *

*   ***null —*** 根本不包含任何值。如果它被赋值给一个变量，那就意味着这个变量没有任何值。它不包含任何东西。所以当一个变量指向 null 时，它不指向任何东西。

*   ***指针—*** 每个变量都有一个内存，每个内存都有自己的地址和位置。指针是一个特殊的变量，它包含了指定变量的地址。它提供了对该变量的值和地址的直接访问。

*   ***空指针—*** 在计算机编程中，空指针是不指向任何对象或函数的指针。

*   ***空指针异常—*** 空指针是运行时异常。当应用程序试图使用包含空值的对象或变量引用时，会引发空指针异常。

在 Java 中，可以直接将 null 赋给任何变量或对象类型。但是它创造了如此多的漏洞和崩溃。科特林提出了一个很好的解决方案。

## kot Lin 如何处理 null？

* * *

*   每个 android 开发者都知道，超过 70%的 android 应用会因为空指针异常而崩溃一次。

*   Kotlin 引入了一种新的安全的方法来处理空值。

*   在 kotlin 中，不能直接给任何变量或对象赋值' null'。

*   ***在 kotlin 中没有变量，默认情况下，可以设置为 null。*T3】**

*   用于区分空变量和其他正常变量。在 kotlin 里还要加上 ***？*** (问号)末变。*这里类型推断不起作用，数据类型必须显式声明。不然以后会产生问题。*

## 编译时检查

* * *

*   记得有一次你用问号声明了一个变量。它将成为一种特殊的变量，只能通过编译时检查来访问。

*   一旦变量被声明为“空变量”，每次你调用它时，你必须检查变量是否包含空值。

*   有两种方法来执行检查:

*   通过 if else 条件

*   通过安全呼叫操作员(？。)

#### 检查是否满足 else 条件

```
val b = "Kotlin"
if (b != null && b.length > 0) {
    print("String of length ${b.length}")
} else {
    print("Empty string")
} 
```

Enter fullscreen mode Exit fullscreen mode

*   如果不先检查它是否为空，它就不会编译。

#### 检查通过安全呼叫操作员

*   这里通过安全呼叫操作符进行检查更加简洁易用。

```
val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length) 
```

Enter fullscreen mode Exit fullscreen mode

*   如果`b`不为空，则返回`b.length`，否则返回`null`。

*   因此，有了这个解决方案，至少你的应用程序不会再通过 **NullPointerException** 隐式崩溃。

## [T1】！！(断言运算符)](#-assertion-operator)

* * *

*   但是考虑这样一种情况，您 100%确定可空变量不包含空值。

*   所以在这种情况下，为了避免检查，你可以使用断言操作符。这将抑制支票。

*   但是在这种情况下，编译器依赖于你，如果这个可空变量包含空值。因此，在这种情况下，您的应用程序将崩溃，编译器将抛出 NullPointerException。

```
val a: Int? = null
val b= a!!.toDouble() 
```

Enter fullscreen mode Exit fullscreen mode

*   但是这个操作符非常危险，它会让你陷入几个小时的调试痛苦中，并且让你的应用程序崩溃。

*   ***所以尽量避免。*T3】**

*   因此，科特林以这种方式处理 ***【十亿美元的错误:】***

今天就到这里，伙计们。感谢阅读。敬请关注更多内容。

在那之前，继续编码，继续爱。

> 想和我联系吗？以下是链接。我很乐意成为你的朋友。😊
> [Twitter](https://twitter.com/jay_tillu)
> [脸书](https://www.facebook.com/jaytillu.1314/)
> [insta gram](https://www.instagram.com/jay.tillu/)
> [Medium](https://medium.com/jay-tillu)
> 或者直接发邮件给我[jayviveki13@gmail.com](mailto:jayviveki13@gmail.com)