# 使用 javascript 的零知识认证

> 原文：<https://dev.to/simbo1905/zero-knowlege-authentication-in-javascript-23lf>

密码是安全的克星，它们永远不应该离开客户端应用程序或 web 浏览器。人们认为他们理解最后一句话，然后使用过时的散列技术来处理密码。开发人员应该使用零知识密码证明库，并采取最大限度的安全。

零知识认证协议到底是什么？这是一种认证协议，其特性是任何观察网络流量的人都学不到任何有用的东西。[安全远程密码协议](https://en.wikipedia.org/wiki/Secure_Remote_Password_protocol) (SRP)是一种零知识认证协议，在 RFC 2945 和 RFC 5054 中有描述。 [thinbus-srp](https://www.npmjs.com/package/thinbus-srp) 是用 JavaScript 编写的 srp 的一个实现。

大多数站点用来处理密码和 API 密钥的典型最佳实践依赖于攻击者不能窥探流量。我们必须利用 HTTPS 来保密。问题是，如果你不使用零知识认证协议，那么 HTTPS 是你唯一的防线。OpenSSL [Heartbleed](https://www.mumsnet.com/features/mumsnet-and-heartbleed-as-it-happened) 漏洞是最引人注目的问题之一，它表明 HTTPS 可能会遇到攻击者获取密码的问题。许多开发人员不会意识到这样的问题。当我们真正了解它们时，它们已经打了补丁。这并不是保护我们自己免受未来漏洞和黑客攻击的巨大动力，因为这些漏洞和攻击还没有明确的现实危险。

更强的动机可能是考虑到软件部署正变得越来越复杂。现代云安全是基于软件配置的，就像其他任何东西一样，软件配置也可能存在缺陷。有了云技术和无服务器，在边缘终止 HTTPS 是正常的。然后，您的网络流量通过由其他公司控制的许多层。即使我们相信他们正在审查他们的员工，也很容易出现泄露未加密流量的错误。任何人的代码都可能有错误处理或日志错误，如果我们将散列密码泄露到中央日志服务中。作为开发人员，我们需要认识到事情一直在变得越来越复杂，我们必须提高级别来保护那些依靠我们来保证他们安全的人。

那么，为什么我们没有听说过零知识协议，为什么我们没有每天使用它们呢？您的浏览器使用零知识协议通过 HTTPS 创建到此 web 服务器的安全连接。web 浏览器和 web 服务器协商一个会话密钥，然后使用该密钥加密 HTTP 请求和响应。如果有人捕获了所有数据包，他们就拥有了用于生成共享会话密钥的所有数据，以及用该密钥加密的所有数据，但是他们无法恢复任何数据。这就是零知识安全的含义。几十年后，我们才默认使用 HTTPS。你打算十年后再在你自己的代码中应用同样的安全级别来验证你的用户吗？

如果你被这个说服了，你可能会想这其中有什么猫腻。答案是零知识协议有更多的活动部分。下面是显示如何使用 thinbus 库对用户进行身份验证的序列图:

[![SRP Auth Sequence Diagram](img/5967944e740f3654f68c3458b4682840.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--h3a4B4I1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/i7tynicwn5wb6r6wsa81.png)

然而，如果您后退一步，这只是从服务器获取 salt 和挑战的额外获取。在服务器上，您需要存储发送给客户端以完成密码验证的独特质询。除此之外，它只是一些普通的旧 JavaScript 函数做加密数学。对于编写到服务器的额外行程和调用加密库的工作，您获得了更多的安全性。你不再仅仅依靠 HTTPS 来保护你的用户免受黑客攻击。是时候升级并开始使用安全远程密码协议了吗？