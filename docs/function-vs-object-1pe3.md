# 功能与对象

> 原文：<https://dev.to/stereobooster/function-vs-object-1pe3>

关于面向对象编程(OOP)和函数式编程(FP)之间的区别有一个正在进行的讨论。我们来谈谈相似点。让我们来谈谈主要的构建模块:函数和对象。

如果我不偷懒，这将是一系列的职位。

## 什么是物体？

我试图找到一个好的定义，但是这比我想象的要难很多资料都在谈论什么是 OOP，但是没有人费心去解释什么是对象。

让我们从 Java 中的[对象定义开始吧，我猜:](https://docs.oracle.com/javase/tutorial/java/concepts/object.html)

> 对象是理解面向对象技术的关键。环顾四周，你会发现许多真实世界的例子:你的狗，你的桌子，你的电视机，你的自行车。
> 
> 现实世界的对象有两个共同的特征:它们都有状态和行为。狗有状态(名字、颜色、品种、饿不饿)和行为(叫、叼、摇尾巴)。自行车也有状态(当前档位、当前踏板节奏、当前速度)和行为(换档位、换踏板节奏、踩刹车)。识别现实世界对象的状态和行为是开始考虑面向对象编程的一个很好的方法。

相当平易近人的定义。我将稍微重新措辞一下。对象是一种状态，带有附加到其上的行为。

## 什么是函数？

我写了两篇关于它的文章:

*   [简介:从函数到闭包](https://stereobooster.com/posts/from-function-to-closure/)
*   [不是函数](https://stereobooster.com/posts/not-a-function/)

让我们用简化的定义(和对象定义一样)并且说功能是一种行为(精确的定义见上面的链接)。

在函数式编程中，他们喜欢将函数作为值来传递，以便能够将函数“转换”成闭包(这里转换不是一个精确的词，因为闭包是一个具有自由变量的函数，但是让我们用一个简化的视图来看)。

什么是[闭包](https://stereobooster.com/posts/demystify-closures/)(编程语言中)？

> 闭包是具有代码和数据组件的数据结构。
> 
> - [闭包转换:如何编译 lambda](http://matt.might.net/articles/closure-conversion/)

我将稍微重新措辞一下。闭包(或作为值的函数)是一种带有状态的行为。(State，在这种情况下是**不可变**。我将任何数据称为状态)

## 等一下🤔

再次比较这两个定义:

*   对象是一种状态，带有附加到其上的行为
*   闭包(或作为值的函数)是一个附加了状态的行为

他们不是一样的吗？

### 我不信。你的证据是什么？

让我们写一些代码。我将使用 JavaScript，因为它支持这两种范式。

```
class DogClass {
  #name;
  constructor(name) {
    this.#name = name;
  }
  bark() {
    return `${this.#name} is a good dog!`;
  }
}
const belka = new DogClass('Belka');
belka.bark(); 
```

*注意*:本例使用[“JavaScript 类字段声明”](https://github.com/tc39/proposal-class-fields#private-fields)建议声明私有字段名称。目前张贴的例子作品在铬。

```
const DogFunction = (name) => {
  return {
    bark: () => {
      return `${name} is a good dog!`;
    }
  }
}
const strelka = DogFunction('Strelka');
strelka.bark(); 
```

*注意*:函数返回记录数据结构(在 JS 中，这个数据结构被命名为“Object ”,但是我们没有使用任何“objecty”特性，我们把它作为一个简单的键值数据结构)。变量`name`私有存储在闭包的作用域中，没有办法在外部访问它。

## 没有新意

如果你仔细想想，这很有意义:所有的计算机都处理状态(数据)和行为。这个想法被反复发现:

Lamport 是这样定义计算的:

> 有几种方法来定义计算。现在，我举一个最简单的例子:**计算是一系列的步骤，我称之为行为**。一个步骤有三种常见的选择，导致**三种不同的行为**:
> 
> *   **动作行为**。步骤是一个动作，它只是一组动作中的一个元素。动作行为是一系列动作。
> *   **状态行为**。一个步骤是一对`(s, t)`状态，其中一个状态是某组状态的一个元素。状态行为是状态的序列`s1 → s2 → s3 → · · ·`。步骤`(si, si+1)`代表从状态`si`到状态`si+1`的转换。
> *   **状态-动作行为**。一个步骤是一个三元组`(s, α, ti)`，其中`s`和`t`是状态，`α`是动作。国家行为是一个序列`s1 -α1→ s2 -α2→ s3 -α3→ · · ·`。步骤`(si, αi, si+1)`表示由动作`αi`执行的从状态`si`到状态`si+1`的转变。
> 
> - [计算和状态机](https://lamport.azurewebsites.net/pubs/state-machine.pdf)。莱斯利·兰波特，2008 年 4 月 19 日

沃思写过《算法+数据结构=程序》这本书。

Ray Toal 写过关于类型的文章:一个类型由一组值和一组允许的操作组成。

## PS

我们没有触及的问题是一个突变。在“纯”FP 中，突变是不允许的。在 OOP 中它们是被允许的。当我说纯的时候，我指的是带有惰性求值和 IO monad 的 lambda 演算，这是一个狭窄的领域`¯\_(ツ)_/¯`。

> 照片由 unsplash 上的 norwood themes 拍摄