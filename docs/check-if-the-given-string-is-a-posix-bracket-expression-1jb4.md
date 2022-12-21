# 📦检查给定的字符串是否是 POSIX 括号表达式。

> 原文：<https://dev.to/samandar/check-if-the-given-string-is-a-posix-bracket-expression-1jb4>

如果给定字符串是 POSIX 括号表达式(POSIX 字符类)
，则返回 True

```
from functorflow import f

print(f('is-posix-bracket', '[foo:]]'))
# False print(f('is-posix-bracket', '[xdigit:]]'))
# False print(f('is-posix-bracket', '[[:xdigit:]]'))
# True print(f('is-posix-bracket', '[[:xdigit:]]'))
# True print(f('is-posix-bracket', '[[:alpha:]123]'))
# True print(f('is-posix-bracket', '[[:alpha:]123]'))
# True print(f('is-posix-bracket', '[a-c[:digit:]x-z]'))
# True print(f('is-posix-bracket', '[:al:]'))
# True print(f('is-posix-bracket', '[abc[:punct:][0-9]'))
# True 
```

Enter fullscreen mode Exit fullscreen mode[https://repl.it/@functorflow/is-posix-bracket?lite=true](https://repl.it/@functorflow/is-posix-bracket?lite=true)