# 用 5 分钟时间了解断路器模式

> 原文：<https://dev.to/azure/learn-about-the-circuit-breaker-pattern-in-5-minutes-1l45>

有许多基础设施设计模式。在这篇文章中，我想深入探讨断路器模式。这种模式的名字来自电气工程和断路器。

## 电气工程中的断路器

电力公司以恒定的电压(根据你居住的国家不同而不同)把电送到你家。电压是推动电子通过电路的力的量度。电流是电子流动的速度。传输电子、灯泡、电脑和其他电器的电线会对电流产生负载，所以整个房子的电阻都不一样。电阻产生热量。

**欧姆定律**定义了这些不同元件之间的关系:

**I = V/R**

*   I -以安培为单位的电流
*   V -电压，单位为伏特
*   R -电阻，单位为欧姆

电路是电流的路径。家用断路器是一种安全机制，通过切断电路或路径来防止火灾。正常工作的断路器在电流跳到不安全的水平之前断开电路。

此外，住宅设计有并联电路，因此单个房间或大型设备的故障与房子的其他部分隔离。过多的电荷和热量可能会使房屋线路或电器线路过载，损坏其他设备或引起火灾。

由于电流不能流动，断开电路就断开了电路。闭路电视按设计运行。

## 软件工程中的断路器

如果我们把请求流想象成电，那么我们通过建立一个中断请求流的机制来实现断路器模式。

当我们在软件中讨论断路器模式时,“开路”电路表示存在问题。在我们的设计中实现断路器的目标是防止个别服务对其他服务造成损害或使整个系统瘫痪。如果请求持续失败，持续重试可能会加剧潜在的问题。它还会延迟恢复。

**什么故障会导致服务中的断路器跳闸？**

在分布式系统中，资源消耗、错误密度或运行时间都可能表明对整个系统有影响的体系结构的局限性。

断路器在软件中的实际实现与在电气工程中有很大不同。当故障不再发生时，我们可以自动解决跳闸的断路器。我们还可以实现第三种状态，“半开”，允许降低性能。在恢复期间，通过半开电路限制请求，为评估故障服务的状态和故障服务的恢复提供了时间。

有没有我们可以为系统定义的欧姆定律？

不存在欧姆定律，但是可以从最大请求率或从属服务和第三方服务的限制方面来考虑。这些服务的总负载是多少？

运营工程师需要知道是否有人实施了断路器以及在哪里实施。根据断路器的实现，客户端可能会完全失败某个特定的操作，或者将请求排队等待以后处理。跳闸的断路器可以为改善可操作性和设计提供方向。暴露和监控断路器的状态变化至关重要。

在某些方面，断路器模式并不理想。我们通常没有一个单一的指标可以告诉我们某个东西是否处于不良状态。在设计我们的应用程序时，提高我们为客户提供的价值，最大限度地减少对外部服务的影响，以及减少浪费的支出都是有益的。基于监控和评估增量改进或定制的单个指标实现断路器可能比什么都没有好。

工程师通常将断路器模式与重试和隔离设计模式结合起来实现。我将在不同的文章中探讨这些模式。