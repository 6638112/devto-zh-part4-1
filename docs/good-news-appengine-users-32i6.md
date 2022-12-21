# AppEngine 用户的好消息。

> 原文：<https://dev.to/saifali40/good-news-appengine-users-32i6>

嗨，伙计们，对于那些正在使用 Google AppEngine 的人来说，有一个好消息(我是作为一名 java 开发人员来写这篇文章的)。

已经在使用 AppEngine 或者了解 AppEngine 的人可以跳过这一段。
Google app engine:Google app engine 是一个平台即服务和云计算平台，用于开发和托管 web 应用程序。(aws-elastic-beanstalk 相当于谷歌云平台)。

在过去的 3 年多时间里，我一直在使用 AppEngine，这很好，因为我们不必管理基础设施，或者不必担心停机。谷歌会帮我们解决这个问题。

这里我要说的是 Google AppEngine 标准环境中没有(官方上仍然没有)的东西，我会列出一些我认为重要的东西。

*)我们不能做非阻塞 I/O
*)线程(没错！，但也有 GCP)
*) GRPC 提供的异步调用的替代选项(AppEngine 使用 jetty 服务器，这就是答案)

现在让我们谈谈好消息吧？
2018 年 9 月甲骨文发布了他们最新的 LTS 版本 Java 11。经过 9 个月的更新，Google 宣布 Google AppEngine 标准测试版将支持 java11。

我猜这将是 AppEngine 的定期更新，现有的限制将保持不变。但是在检查了公告之后，这是相当令人惊讶的。谷歌决定给开发者更多的自由。(是的！).

([https://cloud . Google . com/blog/products/application-development/turn-it-up-to-eleven-Java-11-runtime-comes-to-app-engine](https://cloud.google.com/blog/products/application-development/turn-it-up-to-eleven-java-11-runtime-comes-to-app-engine))。

我读了文档中的以下几行，在那里我更兴奋

 `You’ll also find some changes in the Java 11 runtime. For example, the Java 11 runtime does not provide a Servlet-based runtime anymore. Instead, you need to bundle a server with your application in the form of an executable JAR.` 

我已经通过改变 tomcat jetty 容器在旧版本中捆绑了 Spring boot，效果很好。但我仍然认为局限性是存在的。但是今天早上，我决定用 netty 服务器、非阻塞 I/O 和 AppEngine 线程进行尝试。它如预期的那样起作用了。

我创建了一个 GitHub 存储库来检查如何使用 AppEngine 中的 java11 和 Micronaut(它将 netty 作为默认服务器)[https://github.com/saifali40/micronaut-gcp](https://github.com/saifali40/micronaut-gcp)。

我尝试了以下方法:
为了使用 thread，我使用了 ParallelStream，而没有使用 Flowable (RxJava)。

如果人们有兴趣看看 GRPC 是如何工作的，请在下一篇文章中发表你的评论。