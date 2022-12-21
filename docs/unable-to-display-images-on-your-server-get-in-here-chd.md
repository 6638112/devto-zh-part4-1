# 无法在您的服务器上显示图像？快进来。

> 原文：<https://dev.to/cyprian_dev/unable-to-display-images-on-your-server-get-in-here-chd>

我不知道谁在本地服务器上显示来自 VScode Live 扩展或第三方的图像。我只是放下这个来帮助那些遭受痛苦的人，这些痛苦是我一个多月来一直在与之斗争的，直到昨晚。

在几个平台上发布了我的问题并得到了大量对我没有帮助的术语后，我在谷歌上搜索直到我的大脑几乎从我的头上跳下来，我昨晚做到了(对你来说可能是早上或下午，取决于你的地理位置)。

首先，我意识到文件路径或扩展名对文件元素的行为起着重要的作用。有时，因为计算机很容易为我们弹出东西，我们认为它是一个非常智能的设备，然后当它无法执行我们认为简单的程序时，我们变得非常沮丧，忘记了计算机只是被编程为在给它们的指令参数内思考和行动。

原谅我，我们走吧。从我的经验来看，我意识到服务器只能从自身访问文件，我指的是服务器的根目录，而不是其他地方。因此 xammp 中的 localhost 只能访问从其根目录开始的文件，VScode 扩展也是如此。

如果这一切都令人困惑，让我只是放弃我是如何解决我的问题。将图片与项目中使用的其他文件放在同一个文件夹中。只使用一个简单的名称和全部小写来编辑它们，然后将该名称添加到您的项目中。不要使用完整路径，因为这可能会超出服务器访问文件所需的长度范围。

快乐编码