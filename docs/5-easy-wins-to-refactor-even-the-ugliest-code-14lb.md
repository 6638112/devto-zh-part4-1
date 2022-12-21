# 重构最丑陋的代码的 5 个简单胜利

> 原文：<https://dev.to/mlevkov/5-easy-wins-to-refactor-even-the-ugliest-code-14lb>

当您开始一个新项目时，编写干净的代码可能是一个挑战。尝试在不破坏任何东西的情况下清理现有应用程序中的代码与此类似:

> ![unknown tweet media content](img/31f5340fa901ef8e9f89cd175be9028c.png)![Play butt](img/980e9fb12d58fa9423fc94c33003fc4f.png)<video loop="" controls=""><source src="https://video.twimg.com/ext_tw_video/1150872436944048130/pu/vid/1280x720/_kqaIyy-Bqbfv1wH.mp4?tag=10" type="video/mp4"></video>![Heavenly @EVO 🍑 profile image](img/9497fce2bf924c9faef784270cb05e1a.png)天堂@EVO🍑@ heavenly control![twitter logo](img/65e26e35707d96169ec8af6b3cbf2003.png)如果你用枪指着我的头，让我完成这一关，我会告诉你扣动扳机02:10AM-2019 年 7 月 16 日[![Twitter reply action](img/269095962147c28351274afdd5486a48.png)](https://twitter.com/intent/tweet?in_reply_to=1150950714090278916)[![Twitter retweet action](img/771160ecf06ae3d4d7a7815c29c819c2.png)](https://twitter.com/intent/retweet?tweet_id=1150950714090278916)55961[![Twitter like action](img/c077611ab2a5e0b4cd0c826ee7ae1e48.png)](https://twitter.com/intent/like?tweet_id=1150950714090278916)164660

我已经做了几年技术主管，在那段时间里，我看到了我必须维护或者扩展的大量代码。通过许多令人沮丧的小时和十几只橡皮鸭，我开发了一些提示和技巧来帮助重构最丑陋的代码库。

我列出了 5 个快速成功的例子，你可以应用于任何代码库，或者当你开始一个新项目时记住它们。

每一次胜利都以一个糟糕的代码样本开始，然后是一个好的代码样本，并解释了发生了什么变化。

## 1)没有不变的方法

如果不管传入什么，一个方法总是返回完全相同的东西，那么这个方法可以被认为是无用的。
正如您在示例 invariant-method-bad.ts 中看到的，getName 将总是返回完全相同的“没有找到名称”消息。
我们在 invariant-method-good.ts 方法中通过简单地返回我们想要的结果来解决这个问题。