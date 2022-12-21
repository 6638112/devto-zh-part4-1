# 我对代码挑战#77 的解决方案

> 原文：<https://dev.to/victoravelar/my-solution-to-code-challenge-77-2f5n>

在 golang 实现，公平地说相当容易😄

```
func GetNthFib(n int) int {
    if n == 1 {
        return 0
    }
    if n == 2 {
        return 1
    }
    x, y := 0, 1
    for i := 2; i < n; i++ {
        x, y = y, x+y
    }
    return y
} 
```

Enter fullscreen mode Exit fullscreen mode

## 解释

所以我们检查前两个值，因为这两个值是构建序列其余部分所必需的。

一旦我们知道它不是 0 (x)或 1 (y ),我们就知道正确的结果来自于将 x+y 相加并将值向前移动 1 位。

循环从 2 开始，因为否则结果将会偏移 2 次迭代(我们已经静态地检查了前两次)。

例如，如果循环从 0 开始，他们要求第 n 个 3，那么我们的结果将是 3，这是不正确的，因为斐波那契数列的第三个位置是 1。

你可以使用这个 [Golang 游乐场链接](https://play.golang.org/p/yNUdwd07SvF)来玩它