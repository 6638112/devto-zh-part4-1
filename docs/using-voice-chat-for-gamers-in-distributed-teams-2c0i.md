# 为分布式团队中的游戏玩家使用语音聊天

> 原文：<https://dev.to/tfnico/using-voice-chat-for-gamers-in-distributed-teams-2c0i>

(这是我第一次在 Dev 上发表博文。希望我这样做是对的！我在这里写了原文。)

这是一篇关于分布式团队中实时语音聊天工具的有用性的文章。

如果你看过《魔兽世界》成名的视频，你一定听说过这种工具在起作用。这是视频中的参与者如何相互交谈——这不是魔兽世界游戏内置的功能——这是一个单独的面向团队的网络电话软件，它完全是为了让游戏玩家在游戏时进行口头交流。

因为这些工具是为游戏玩家设计的，所以它们必须是

*   快速(低延迟)
*   轻量级(为了不从繁重的游戏图形中窃取 CPU 周期)
*   适度的带宽使用(为了不影响游戏服务器连接)有几个选择: [TeamSpeak](https://teamspeak.com/en/) ， [Ventrilo](http://www.ventrilo.com/) ，最近大规模增长的 [Discord](https://discordapp.com/) ，最后 [Mumble](https://wiki.mumble.info/) ，这是该团伙的开源替代方案。几年前，当我[加入 eyeo](https://blog.tfnico.com/2017/01/joining-eyeo.html) (一家分布式公司)时，几个运营团队都是狂热的游戏玩家，他们之间建立了一个 TeamSpeak 服务器，允许在在线游戏会话期间进行语音聊天(顺便说一下，这是分布式团队的一个很好的团队建设选项)。

随着团队的成长，我们开始尝试在会议间隙使用这项服务进行团队交流(我们在某个时候改用了 Mumble，所以从现在开始我称之为 Mumble)。

[![File:Metromumble dark preview.png](img/b470a1fbd5d149a28a6022be18f2948f.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--t1uIWeX3--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://wiki.mumble.inimg/3/34/Metromumble_dark_preview.png)

与我们传统的视频会议软件(我们使用蓝战士)相比，Mumble 找到了一个非常好的切入点:

视频会议需要多次点击才能启动，并让每个人都参与进来。

另一方面，Mumble 让团队一直保持联系，所以只需点击一下就可以开始讲话。

通常的情况是这样的:

1)我在 IRC 上 ping 某人，问一个问题

2)我们来回写几行

3)我们中的一个会问“mumble？”

4)我们俩都在喃喃自语中解除静音，开始说话

5)其他人可能会听着，如果他们喜欢，就加入谈话，或者如果他们想专注于其他工作，就调到繁忙的频道。

**视频会议软件将占用所有带宽和资源**

视频会议软件被优化为模拟物理存在，它将最大限度地利用你的笔记本电脑资源，有时会产生毁灭性的影响(尤其是在 Linux 上)。

而 Mumble 则完全牺牲视频，只专注语音。它被优化以节省资源，所以你几乎不会注意到它正在运行。

视频会议不适用于糟糕的连接(或者需要你通过昂贵的电话号码拨号)。

另一方面，Mumble 在较差的连接上表现出色。延迟非常低，可以通过“乒乓测试”来测试:

1)你说“乒”

2)对方听到你说“乓”

3)你听到他们说“乓”

时你说“乒”4)重复，直到你感觉到往返一次需要多长时间

在我们的视频会议系统中，一次往返大约需要 1-2 秒钟。).

在 Mumble 中，就像坐在另一个人旁边一样，你几乎注意不到延迟，即使是在与地球另一端的同事通话时(上周五，我与一位在叶卡捷琳堡的同事和另一位在印度的同事进行了 ping 测试)。

我认为这种延迟的差异可能会对大型分布式群体中的自然讨论产生巨大影响，但这是另一种理论。

因此，事实证明，让游戏玩家喜欢 Mumble 的东西也可能让分布式团队喜欢 Mumble。

**如果你现在就想和你的团队一起尝试一下**，你可能最好从 Discord 开始，因为这是一个免费且简单的设置。然而，在 eyeo，我们在安全和隐私等问题上非常坚定，所以我们很高兴可以在自己的服务器上使用令人敬畏的开源 Mumble。