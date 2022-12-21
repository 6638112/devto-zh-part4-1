# Dart 中的 Lambda 函数

> 原文：<https://dev.to/jay_tillu/lambda-functions-in-dart-3eih>

*   Lambda 是表示小函数的一种简洁明了的方式。

*   λ函数也称为箭头函数。

*   但是这里要记住，通过使用 Lambda 函数的语法，你只能返回一个表达式。它必须只有一行表达式。就像普通函数一样，lambda 函数不能有一个代码块来执行。

*   简而言之，如果你的函数只有一个表达式要返回，那么为了快速地用一行代码表示它，你可以使用 lambda 函数。

#### 语法

```
return_type function_name(arguments) => expression; 
```

Enter fullscreen mode Exit fullscreen mode

*   这里还要注意，我们不需要显式的 return 语句。

#### 程序

```
int ShowSum(int numOne, int numTwo) => numOne + numTwo;

main() {
  print(ShowSum(10, 20));
}

Output
30 
```

Enter fullscreen mode Exit fullscreen mode

这就是 lambda 函数的内容。请考虑一下这个概念。另外，如果我错过了什么，请随时告诉我。直到那时，继续爱，继续编码。我一定会在下一篇文章中介绍您。

记住没有老师，没有书，没有视频教程，也没有博客能教会你一切。有人说，学习是一个旅程，旅程永无止境。只是从这里那里收集一些数据，读一读，学一学，练一练，试着去应用。不要因为做不到或者不知道这个概念或者那个概念而犹豫。记住，每个程序员都是从你现在走的这条路上走过的。记住每个大师都曾经是初学者。努力工作，全力以赴。

### 欲了解更多信息，请访问以下链接

*   [Fuchsia OS 官方网站](https://fuchsia.dev/)
*   [Dart 官方网站](https://dart.dev/)
*   [颤振官方网站](https://flutter.dev/)

> 想和我联系吗？以下是链接。我很乐意成为你的朋友。😊
> [Twitter](https://twitter.com/jay_tillu)
> [脸书](https://www.facebook.com/jaytillu.1314/)
> [insta gram](https://www.instagram.com/jay.tillu/)
> [Medium](https://medium.com/jay-tillu)
> 或者直接在[jayviveki13@gmail.com](mailto:jayviveki13@gmail.com)给我发邮件