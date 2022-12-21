# 布尔-好的，坏的，没有丑陋的地方

> 原文：<https://dev.to/macsikora/boolean-the-good-the-bad-and-there-is-no-place-for-the-ugly-2o0h>

布尔型，布尔型，我们都知道那种类型。在我所知道的每一种编程语言中，它都是一种原始类型。Bool 是一种包含两个可能值的类型——True 和 False。这意味着布尔是一个非常小的可能性集。Bool 的这个属性是它的长处，如果 Bool 在该用的时候用，但用错的时候也是最大的弱点。

## 我会努力说服你，在用布尔来代表一个国家的一部分之前，你应该三思而行。

假设我们有`User`，我将使用 TypeScript 符号编写用户契约。此外，本文中的代码示例将使用 TS。希望你不介意，这将是足够的可读性。

```
type User = {
  id: string
  name: string
} 
```

Enter fullscreen mode Exit fullscreen mode

好的，很简单。现在，业务部门表示，我们在其他用户中也有 admin，这些用户有不同的功能。啊哈，所以最简单的方法就是创建一个标志。下面的用户有这个小小的变化

```
type User = {
  id: string
  name: string
  isAdmin: boolean
} 
```

Enter fullscreen mode Exit fullscreen mode

很好，所以在现在的代码中，很容易检查用户是否是管理员。我将创建一个函数来检查

```
const isAdmin = (user:User) => user.isAdmin 
```

Enter fullscreen mode Exit fullscreen mode

不是很复杂，但是让我们继续。好了，现在我们有了不同的行为，让我们假设相当多的代码是使用我们的`isAdmin`标志完成的。之后，企业找到我们说——我们也有主持人。版主是不同于普通用户或管理员用户的用户。废话，我们现在能用我们的`isAdmin`旗做什么。让我们继续使用这些布尔函数，并创建另一个

```
type User = {
  id: string
  name: string
  isAdmin: boolean
  isModerator: boolean
} 
```

Enter fullscreen mode Exit fullscreen mode

很好，但是，不完全是。问题是代码在状态属性之间引入了隐藏的依赖关系。哪里哪里？是的，所以依赖关系在`isAdmin`和`isModerator`之间，因为用户不能同时是版主和管理员(即业务)。好，考虑到这一点，看起来存在冲突状态，我需要保护应用程序不受这种状态的影响。冲突的国家是

```
isAdmin: true, isModerator: true 
```

Enter fullscreen mode Exit fullscreen mode

这是不可能发生的，但是类型并没有说它不能。从类型的角度来看，它是完全有效的形状。让我们在代码中解决这个问题，并创建函数来创建不同类型的用户。

```
/* ... - is not spread operator but just a placeholder, I just skip rest of the code */
const createNormalUser = (...) => ({.., isAdmin: false, isModerator: false})
const createModeratorUser = (...) => ({.., isAdmin: false, isModerator: true})
const createAdminUser = (...) => ({.., isAdmin: true, isModerator: false}) 
```

Enter fullscreen mode Exit fullscreen mode

好吧，我们得救了，但只是暂时的:(。过了一段时间，又有了新的要求。第四类用户管理器。糟糕，比上次更糟糕。对于两个布尔量的组合是- `2 power 2 = 4`，那么对于三个布尔量的组合已经是`2 power 3, so 8`。和更多的冲突状态，对于三布尔来说，有这样的冲突状态

```
isAdmin: true, isModerator: true, isManager: true
isAdmin: false, isModerator: true, isManager: true
isAdmin: true, isModerator: false, isManager: true 
```

Enter fullscreen mode Exit fullscreen mode

所以对于 8 个组合，4 个正好无效[(真，真，真)，(真，假，真)，(假，真，真)，(真，真，真，假)]。在这个时候，你应该明白这是怎么回事。下一个需求给了我们 16 种组合，依此类推。这种方式在这种情况下是不可持续的。应该怎么做呢？

## 自定义救援类型。

让我们去掉布尔的限制，适当地设计状态。事实是我们用户可以有不同的类型。所以合适的型号应该是

```
type User = {
  id: string
  name: string
  userType: UserType 
}
type UserType = 'Admin' | 'Normal' | 'Moderator' | 'Manager' 
/* Yes, UserType can be also represented as Enum type */ 
```

Enter fullscreen mode Exit fullscreen mode

太好了！没有冲突的状态。我们现在可以通过
轻松检查用户类型

```
user.userType === 'Admin' 
```

Enter fullscreen mode Exit fullscreen mode

也可以在函数
中抽象

```
const isAdmin = (user: User) => user.userType === 'Admin' 
```

Enter fullscreen mode Exit fullscreen mode

如您所见，与 check
相反，它也更加明确

```
!u.isAdmin && !u.isModerator && !u.isManager // it means it is normal user 
```

Enter fullscreen mode Exit fullscreen mode

您已经:

```
u.userType === 'Normal' 
```

Enter fullscreen mode Exit fullscreen mode

甜食😉

好了，我们通过这种方法得到了什么:
✅它是可扩展的
✅它消除了冲突的状态形状
✅它更加明确
✅它消除了检查许多布尔型字段的复杂性

让我们来看标题布尔——好的，坏的和，什么都没有。布尔可以是好的也可以是坏的，只有两种可能，所以西方著名的(好的、坏的和丑的)主要人物的定义不能用布尔来表示。再次需要自定义类型😁

```
type CharacterType = "Good" | "Bad" | "Ugly" 
```

Enter fullscreen mode Exit fullscreen mode

亲爱的读者，下次不要选择 Bool 作为默认。也许需要一个自定义类型:)