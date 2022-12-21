# 多米诺骨牌如何颠覆无障碍网络——第 1 部分:公共住宿

> 原文：<https://dev.to/bendmyers/how-domino-s-could-topple-the-accessible-web-part-1-public-accommodations-29pp>

本文是关于美国案例法中网页可访问性的三部分系列文章的第一部分，以及罗伯斯诉达美乐比萨案对该领域的影响。这第一个条目集中于法院解释公共便利的方式。

你也可以在我的博客上阅读这篇文章[。](https://blog.benmyers.dev/dominos-1/)

## 发生什么事了

去年，美国有 2285 起网络无障碍案例。也就是一天 6 起左右，几乎是 2017 年的 3 倍。^1 随着案件数量的上升，媒体的关注度也在上升，没有一个案件像罗伯斯诉达美乐比萨案那样吸引了公众的关注。

吉列尔莫·罗伯斯有着传奇般的三年。作为一个使用屏幕阅读器浏览网页的盲人，他发现自己无法从达美乐订披萨。他在 2016 年 9 月对达美乐提起诉讼，指控达美乐的网站和移动应用程序与他的屏幕阅读器不兼容。加州中央区驳回了此案，理由是法律不够具体，不足以让达美乐承担责任。第九巡回上诉法院在 2019 年 1 月推翻了这一驳回，声称法律事实上确实要求披萨连锁店对无法访问的网站和应用程序负责。最近，在 7 月，达美乐公司请求将此案提交最高法院。他们得到了美国商会、餐馆法律中心和全国零售联合会的支持。^2 的企业真的，真的希望看到这个案子按照他们的方式发展。

这个案例可能会对许多残疾互联网用户产生持久的影响。最高法院还没有看到一个网页可访问性的案例，这意味着下级法院已经被留下来自己解决这个问题。具体来说，法院一直在努力解决两个大问题:

1.  美国法律要求网站无障碍吗？
2.  如果是，网站遵循哪些可访问性标准？

法院对这些问题的许多回应导致了许多困惑、含糊和沮丧。然而，了解这些法院的来源对于理解残疾用户访问互联网的未来至关重要。

让我们看看第一个问题:

## 法律是否要求网页无障碍？

没有联邦法律提到网页可访问性。结果，法院转向了退而求其次的办法:美国残疾人法案。《美国残疾人法》第三章禁止公共场所歧视美国残疾人:

> “任何个人在充分和平等地享受任何公共住宿场所的商品、服务、设施、特权、优势或便利方面，不得因残疾而受到任何拥有、出租(或租赁给)或经营公共住宿场所的人的歧视。”

残疾原告认为，网站被视为公共场所，因此不能被访问。

### 什么是公共住宿？

正是在这里，“公共住宿”的定义将是非常好的。然而，第三章没有提供答案。相反，它提供了一长串公共住宿的例子，包括酒店、餐馆、银行、旅游服务、动物园、自助洗衣店等等。这份清单显然不是详尽的。然而，^3 至关重要的是，它没有提到网站。

### 那么，网站是公共住宿吗？

法院在这个问题上存在分歧，但它们的意见可以大致分为三类:

1.  是的，网站是公共场所。
2.  不，网站不是公共场所。
3.  网站有时是公共场所。

这些意见冲突很多，这意味着有很多案件的裁决不一致。

* * *

#### 观点 1:是的，网站是公共场所

在法院中，认为网站本质上是公共场所的观点是最边缘的。这些法院，即第一和第七巡回上诉法院，认为网站仅仅因为提供了一种服务，就是公共设施。

法院认为，非物质空间被算作公共住宿是有先例的。他们擦掉了一个旧案例的灰尘，ADA-wise:1994 年 Carparts Distribution Center，Inc .诉新英格兰汽车批发商协会案。在 Carparts 案中，第一巡回法院裁定《美国残疾人法案》涵盖了基于电话的服务。他们注意到国会已经将旅游服务列入了公共住宿的范例清单。当时，旅游服务行业很大程度上是基于电话的，所以第一巡回法庭推断*显然*国会打算包括非物质空间，如电话线。

在 Carparts 的裁决中，第一巡回法庭指出:

> "得出进入办公室购买服务的人受《反倾销法》保护，但通过电话或邮件购买同样服务的人却不受保护的结论是不合理的。国会不可能打算这样一个荒谬的结果。”
> 
> ——Ctr 第一巡回上诉法院。汽车批发商的屁股。

第七巡回法院将这一推理应用于一家在线销售其服务的保险公司:

> “被告要求我们从字面上解释‘公共住宿’,以表示一个实体场所，如商店或旅馆，但我们已经拒绝了这种解释。保险公司不能拒绝通过互联网向残疾人出售保险单，就像家具店不能拒绝向进入该店的残疾人出售家具一样。”
> 
> ——第七巡回上诉法院，[摩根诉共同管理。Bd。](https://scholar.google.com/scholar_case?case=731343607554833896)

[网飞](https://scholar.google.com/scholar_case?case=15520314324288957354)、[斯克里布](https://scholar.google.com/scholar_case?case=8523925640371825721)、[蓝围裙](http://www.nhd.uscourts.gov/sites/default/files/opinions/17/17NH236.pdf)都发现自己成了这个意见的接受方。

* * *

#### 观点 2:不，网站不是公共场所

如果第一巡回法院的 Carparts 裁决对你来说有点牵强，你并不孤单。

持这种观点的法院，如第三、第五和第六巡回法院，指出了《美国残疾人法》的完整措辞:“公共住宿场所”他们认为，网站等非物质空间不是地方，因此不在第三章的涵盖范围之内。声称他们被包括在内会极大地扩大法律的范围:

> “在这里，要纳入目前起草的《美国残疾人法》的范围，公共场所必须是有形的混凝土结构。将《美国残疾人法案》扩展到‘虚拟’空间将是在没有明确标准的情况下创造新的权利。”
> 
> ——佛罗里达南区地方法院， [Access Now，Inc .诉西南航空公司](https://scholar.google.com/scholar_case?case=9596654457159505828)

全面披露:在西南航空公司一案中，佛罗里达南区实际上支持第三号意见。这一行恰好是观点 2 的一个非常简洁的解释。

这些法院经常明确拒绝 Carparts 案的裁决，认为这是越权行为:

> “在得出这一结论时，第一巡回法庭忽视了建筑的法定标准，即无社会。[...[英语泛读材料社会主义的教义告诉我们...术语在相关词语的上下文中进行解释，以避免无意中扩大国会法案的范围。'' [...]12181(7)【公共住宿实例列表】中的词语的明确内涵是，公共住宿是一个物理场所。12181(7)和(F)小节中列出的每个术语都是向公众开放的实际场所。”
> 
> 第六巡回上诉法院，帕克诉大都会人寿保险公司。公司，引文省略

提出类似论点并在这些法院中用作判例的其他案件包括[福特诉先灵葆雅公司](https://scholar.google.com/scholar_case?case=11431374417764636751)和[韦耶诉二十世纪福克斯电影公司](https://scholar.google.com/scholar_case?case=16043862805835728767)。

此外，自互联网兴起以来,《美国反倾销法》已经修订了几次。如果国会真的打算让《美国残疾人法案》涵盖网站等非物质空间，他们肯定会在修正案中包括这一点，对吗？四

* * *

#### 观点 3:网站是*有时是*公共场所

最常见的关于网站是公共场所的法院意见是声称网站可以是公共场所的延伸，从而完全回避了这个问题。

> “虽然地区法院在这个问题上存在一些分歧，但似乎大多数法院都认为网站不受《美国残疾人法案》的保护，除非网站上的某些功能妨碍了物理空间的充分使用和享受。”
> 
> —佛罗里达州南区地方法院， [Gomez 诉 Bang & Olufsen Am。，Inc.](https://www.devinemillimet.com/getmedia/e026ae60-63c1-4895-abe8-42c5826d42fa/Gomez-v-Bang-Olufsen-Am-_-Inc-_-2017-U-S-Dist-LEXI.pdf)

这是 nexus 的原则:如果一个网站与一个实体公共场所提供的商品和服务有重要联系，那么该网站就被视为公共场所的延伸。在这种情况下，它将受制于标题三。毕竟，第三章禁止阻碍货物和服务进入任何公共住宿场所的“**”，而不是**任何公共住宿场所的“**”**

第一次全面开展的关于网络无障碍的联邦审判是 2017 年的 [Gil v. Winn-Dixie](https://scholar.google.com/scholar_case?case=6744502269111605689) 。温-迪克西在他们的网站上提供数字优惠券，这些优惠券只能在他们的实体店中兑换。此外，温-迪克西给顾客提供了在线配药的选择，但配药也必须在店内进行。佛罗里达州南部地区认为，温-迪克西网站因此与实体特许经营有关联。因此，网站与屏幕阅读器的不兼容违反了 ADA。5

Nexus 确实反其道而行之。例如，在[厄尔诉易贝公司](https://scholar.google.com/scholar_case?case=13814511373260202940)一案中，一名失聪的原告起诉易贝，因为她不能使用该网站基于手机的供应商验证服务。第九巡回法院裁定，由于易贝没有任何面向消费者的实体场所，易贝不是公共场所，不受第三章的约束。^6 [网飞](https://scholar.google.com/scholar_case?case=627192113961347360)、[维亚康姆](https://scholar.google.com/scholar_case?case=3753744983787595468)、[脸书](https://scholar.google.com/scholar_case?case=14196698777849520612)和[西南航空](https://scholar.google.com/scholar_case?case=9596654457159505828)也被以类似的论点辩护。

今年一月，第九巡回法院推翻了地方法院对罗伯斯案件的驳回，就像在温-迪克西案中所做的那样，将 nexus 论点应用于多米诺案:

> “达美乐的网站和应用程序有助于获取公共住宿场所的商品和服务，即达美乐的实体餐厅。这是订购达美乐产品的两种主要(也是大量广告宣传的)方式，可以在达美乐餐厅取货或送货。我们同意本案中的地区法院的意见，以及在类似情况下面临这一问题的许多其他地区法院的意见，即 ADA 适用于达美乐的网站和应用程序，这些网站和应用程序将顾客与达美乐实体餐厅的商品和服务联系起来。”
> 
> 第九巡回上诉法院，[罗伯斯诉达美乐比萨](https://scholar.google.com/scholar_case?case=14468696865090361672&hl=en&as_sdt=6,44#p905)

* * *

## 外卖

罗伯斯诉达美乐比萨案只是众多围绕美国法律是否要求网站无障碍的法庭案件之一。随着法院在这个问题上继续给出不同的意见，与网页可访问性相关的诉讼数量只会增加。

通过对第九巡回法院的判决提出上诉，达美乐比萨给了最高法院一个机会，最终确认网站是否本质上是公共设施，它们是否本质上不是公共设施，或者如果存在联系，它们是否算作公共设施。

然而，尽管 ADA 是否覆盖网站的问题很重要，但这并不是达美乐争论的唯一问题。请继续阅读第 2 部分，我们将介绍神奇的清单和正当程序。

## 脚注

^1 国家法律评论，[当好网站变坏:网站易访问性诉讼的风险越来越大](https://www.natlawreview.com/article/when-good-sites-go-bad-growing-risk-website-accessibility-litigation)

^2《华盛顿邮报》，[残疾人的保护在网上适用吗？多米诺要求高等法院。](https://www.washingtonpost.com/politics/courts_law/do-protections-for-people-with-disabilities-apply-online-dominos-asks-high-court/2019/07/20/984c685e-a7fd-11e9-a3a6-ab670962db05_story.html)

从某种程度上说，是^3。列出的 12 个子类别是相当固定的，但足够多的子类别包括“或其他 X”从句，这份清单是相当开放的解释。

弗吉尼亚州东区^4 地区法院， [Carroll 诉西北联邦信用合作社](https://news.cuna.org/ext/resources/NewsNow/2018/2018/January/Carroll-v-Northwest-Fed-CU---17cv1205---Order.pdf)

佛罗里达州南区^5 地区法院， [Gil 诉 Winn-Dixie](https://scholar.google.com/scholar_case?case=6744502269111605689)

^6 第九巡回上诉法院，[厄尔诉易趣公司](https://scholar.google.com/scholar_case?case=13814511373260202940)