# Dart 中的用户定义函数

> 原文：<https://dev.to/jay_tillu/user-define-function-in-dart-1a5l>

用户自定义函数是程序员根据自己的需求创建的函数。它为我们提供了重用代码和将代码分成小块的灵活性。让我们讨论如何在 dart 中创建用户定义的函数。

首先，请记住，函数的使用背后有两个主要术语:

1.  函数定义
2.  函数调用

*   **函数定义-** 是我们定义一个函数的时候。这时我们定义它的名字、工作、参数和它的返回类型等。

*   **函数调用-** 这是我们需要函数的时候，我们调用它。请记住，在调用函数之前，您需要定义它。简而言之，首先定义，然后函数调用函数。

用户定义函数基本上有四个部分:

1.  函数名
2.  参数
3.  返回类型
4.  功能体

## 功能定义

* * *

这是我们定义一个函数的时候。这时我们定义它的名字、工作、参数和它的返回类型等。

#### 语法

```
function_name() {
  //statements
} 
```

Enter fullscreen mode Exit fullscreen mode

#### 举例

```
SayMyName () {
  print("Jay Tillu");
} 
```

Enter fullscreen mode Exit fullscreen mode

## 函数调用

* * *

这是我们需要函数并调用它的时候。请记住，在调用函数之前，您需要定义它。简而言之，首先定义，然后函数调用函数。

#### 语法

```
function_name () 
```

Enter fullscreen mode Exit fullscreen mode

#### 举例

```
SayMyName () 
```

Enter fullscreen mode Exit fullscreen mode

## 样本程序

```
SayMyName(){
  print("Jay Tillu");
}
main(){
  SayMyName();
}

Output
Jay Tillu 
```

Enter fullscreen mode Exit fullscreen mode

*   这里我们首先定义函数，然后从主函数中调用它。

这是函数家伙的基础。在接下来的文章中，我们将进一步讨论函数。直到那时，继续爱，继续编码。我一定会在下一篇文章中介绍您。

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