# 有什么计划？

> 原文：<https://dev.to/quinncuatro/what-s-the-plan-19e7>

# 当众学习 DevOps

## 有什么计划？

本着在公共场合学习的精神，我想分享为什么我选择 Kubernetes 作为我的深度潜水的主题，我在这个月底的既定目标是什么，以及为了让我越过终点线，我的学习计划是什么。

短短一个月能感觉到，这是一场马拉松；不是短跑。让我们把这些按顺序排好:

#### 1。我为什么选 K8s？

我有一个有点奇怪的背景:没有计算机课程的高中计算机呆子->尚普兰学院 CNIS 学生->美国法院 DBA>美国法院 web 开发人员->美国法院 AO 的 web 和基础设施开发人员-> Clarity Software Solutions 的 DevOps 工程师。

也就是说，我对创建、部署和扩展 web 应用程序的所有技术都有一定的了解。

万事通，无所不能。

我最初受雇于法院，帮助一个重大的平台升级，就像政府工作一样，被搁置了两年。我最后花了那段时间自学编码。在构建一些小型 LAMP 应用程序来帮助人力资源部门自动化任务时，我发现自己在重新构建服务器来管理 PHP 版本冲突。

在某一点上，我意识到一定有比手动工作更好的方法。就在那时，我得到了一份兼职，在当地的开发者训练营教书。当我得到报酬去学习新的技能，然后传授给我的学生时，我偶然发现了 Docker。

它让我大吃一惊，我可以把这么多不同的容器塞进这么小的空间，而且再也不用担心依赖冲突了。这就是我不断重建服务器的结局！我深入研究了 Docker，甚至在 2017 年纽黑文 GDG 开发者大会上举办了一场关于其使用的研讨会。SCSU 大学计算机科学系主任实际上利用了她在那次研讨会中学到的东西，开始为她的学生将她的实验室环境集装箱化。又一个教学是最好的学习方式之一的例子。

在我和其他开发人员在美国法庭上大肆宣扬容器是未来之后，我们终于让华盛顿的人们为我们建立了一个全国性的 OpenShift 环境。游戏开始。这为我们在自己地区开发的小应用程序走向全国打开了大门。我被送往全国各地的会议(明尼阿波利斯、凤凰城和华盛顿特区)，谈论我的项目，并向其他司法开发人员承诺将容器技术实现到他们的工作流中。使用 OpenShift 使我们不必担心正常运行时间、可扩展性或持久存储。一切正常。那是瓶中的闪电。

我在司法部门的四年经历在我们为我们的法官建造的晨景仪表板上达到了顶峰。我们能够每天早上为每位评委节省大约一个小时的时间。当你看看他们的薪水和我们国家有多少法官时，这个工具每年为司法部门节省了价值数千万美元的停机时间。如果没有像 OpenShift 这样的容器和编排平台，这是不可能的。

在与 OpenShift 合作了一年之后，并且让仪表板达到了其他开发人员可以继续推出它的程度，我不得不离开了那份工作。事实上，我之所以能得到现在的职位，是因为我在法庭上积累了丰富的经验，能够将传统技术融入到容器中，并向外扩展。(我将在本月晚些时候发表一篇有趣的帖子，讨论如何让 Vue、ColdFusion、MySQL 和 Node 在容器中协同工作)。

我的新公司刚刚开始在整个组织内采用 DevOps 原则的旅程。为了减轻开发人员和发布工程师的负担，我们已经准备好将一些内部工具和流程放入容器中自动运行。

我们越能自动化，我们的开发人员就越能创新，我们就能发展得越快。

在这种情况下，我想尽可能多地了解容器编排系统的工作原理。像 Kubernetes 这样的工具将是我的组织取得成功的关键，我希望能够卷起袖子，在未来几年我继续我的 DevOps 布道时帮助解决一些实质性问题。

#### 2。这个月我实际上希望完成什么？

我有一些容器化的工具，这些工具是我在 Clarity 工作期间开发的，已经为我的团队每天节省了很多时间。这很好，因为即使我们把时间追回来了，我们仍然忙得不可开交。

然而，这些仍然是我们必须手动启动、手动启动和手动关闭的工具。

到 7 月底，我希望有一个构建好的 Kubernetes 集群(即使它在我的 MBP 上是本地的),可以运行我的各种工具容器。

我想了解如何建立集群，如何管理集群，以及在出现问题时如何调试集群。Kubernetes 将成为推动我的组织走向自动化启蒙的关键技术，我希望对我的工具有一个深入的了解。

我学到的关于过程自动化、Bash 的任何其他东西都将纯粹是小菜一碟。

#### 3。我的学习计划是什么？

我最初想在这个月读完这本书[经典 Shell 脚本](http://shop.oreilly.com/product/9780596005955.do),但是事情发生了变化。

就在昨天，我决定改做 Kubernetes，所以我不得不稍加修改。

在 Twitter、/r/DevOps 和我的各种 Slack 小组收集了人们的意见后，我找到了 Nigel Poulton 的 Kubernetes 的书。看起来这是从头开始学习的好方法。我还从 O'Reilly/NGinx 找到了一本很棒的免费电子书，名为[Cloud Native devo PS With Kubernetes](https://www.nginx.com/resources/library/cloud-native-devops-with-kubernetes/)。

这些，再加上凯尔西·海托华的教程[Kubernetes-The-Hard-Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)应该为我理解管理我自己的 Kubernetes 集群的来龙去脉提供了一个很好的基础。

我希望阅读这两本书，完成该教程，并在 7 月底之前用代码建立和捕获我自己的集群。我的想法是仍然与你们所有人分享我每天学到的东西，以便将这些知识传递给我的后人。也许这将成为建立第一个集群的好资源。

谁知道这要喝多少杯咖啡。到目前为止，头两天我们有五个。

* * *

我明天会带些技术上的东西回来。在那之前，保持冷静。

[https://Henry needs . coffee](https://henryneeds.coffee)
[博客](https://henryneeds.coffee/blog)
[LinkedIn](https://linkedin.com/in/henryquinniv)
[Twitter](https://twitter.com/quinncuatro)