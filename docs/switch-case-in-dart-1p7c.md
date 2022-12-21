# 省道开关盒

> 原文：<https://dev.to/jay_tillu/switch-case-in-dart-1p7c>

*   一个 ***switch*** 语句是 ***else if 语句*** 的替代语句，它允许对一个变量的值列表进行相等测试。

*   每个值被称为一个 ***情况*** ，并且针对每个开关情况检查被接通的变量。

*   只要表达式值与 case 值匹配，就会执行 case 的主体。

*   使用 ***断开*** 语句终止开关。这里 break 语句是强制性的。否则，dart 分析引擎将抛出语法错误。

*   只有默认情况下，大小写分隔符是可选的。否则，在任何情况下休息都是强制性的。

### 语法

* * *

```
switch (expression) {
  case ONE:
    {
      statement(s);
    }
  break;

  case TWO:
    {
      statement(s);
    }
  break;

  default:
    {
      statement(s);
    }
} 
```

Enter fullscreen mode Exit fullscreen mode

#### 规则的切换情况

*   ***默认*** 的情况是可选的。

*   所有 case 表达式必须是唯一的。
    case 语句只能包含常量。它不能是变量或表达式。

*   变量的数据类型和 case 表达式必须匹配。

*   在一个开关中可以有任意数量的 case 语句。

#### 样本代码

* * *

```
void main() {
  var grade = "A";

  switch (grade) {
    case "A":
      {
        print("Excellent");
      }
      break;

    case "B":
      {
        print("Good");
      }
      break;

    case "C":
      {
        print("Fair");
      }
      break;

    case "D":
      {
        print("Poor");
      }
      break;

    default:
      {
        print("Invalid choice");
      }
      break;
  }
} 
```

Enter fullscreen mode Exit fullscreen mode

所以，伙计们，这就是你们所需要知道的开关盒。如果我错过了什么，请让我知道。我很乐意向你学习。直到那时，继续爱，继续编码。我一定会在下一篇文章中向您介绍。

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