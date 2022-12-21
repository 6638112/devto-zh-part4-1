# 在 Dart 中循环时

> 原文：<https://dev.to/jay_tillu/while-loop-in-dart-21og>

*   **While 循环**是一种不定循环。

*   while 循环执行代码块，直到条件为真。

*   当我们不知道循环将在运行时实际执行多少次时，我们通常使用 while 循环。

*   简单来说，当循环的迭代次数已知时，我们主要使用 for 循环，当迭代次数未知时，我们使用 while 循环。

### 语法

* * *

```
while (condition) {
  //Statements to be executed if the condition is true
} 
```

Enter fullscreen mode Exit fullscreen mode

### 程序

* * *

```
main() {
  int number = 0;

  while (number < 10) {
    if (number % 2 == 0) {
      print(number);
    }
    number++;
  }
}

Output
0
2
4
6
8 
```

Enter fullscreen mode Exit fullscreen mode

这就是 while loop 的家伙。如果我错过了什么，请随时和我分享，我很乐意向你学习。

直到那时，继续爱，继续编码。和往常一样，我一定会在下一篇文章中赶上您。

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