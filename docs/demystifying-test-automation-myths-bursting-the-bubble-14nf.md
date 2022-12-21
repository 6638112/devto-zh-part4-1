# 揭开测试自动化的神秘面纱:打破泡沫！

> 原文：<https://dev.to/ranjanirambles/demystifying-test-automation-myths-bursting-the-bubble-14nf>

鉴于我们的世界正在缩小到可以放入我们手掌的程度，有许多公司正在投资开发以移动为中心的产品。因此，自动化变得越来越重要，因为这些公司希望更快地发展！但是误解仍然盛行。

让我们来解决它们:
100%自动化所有的测试用例:自动化对于更快地前进是必不可少的，但是我们需要认识到我们想要自动化什么。除了维护之外，设计和开发测试框架总是要付出努力的。因此，人们应该考虑每一个需要自动化的测试用例的 ROI。例如:如果一个特定的测试用例需要一个工具来集成你的 android 应用程序的图片库，而目前你的测试框架不支持它，那么你应该问自己的问题是:“自动化这个测试用例会有什么影响”？或者换句话说，“这是 P0 测试用例吗？”
我们测试移动应用，所以我们只关心 UI 自动化:测试涉及多个层面。它可以是 A/B 测试、可访问性测试、API 测试、集成测试、验收测试、性能测试、负载测试等等。同意 UI 是移动应用的主要组成部分，但如果其他集成不能正常工作，它就不能正常工作。如果你的应用与任何硬件/可穿戴设备集成，或者如果你的应用与语音助手集成，那么添加集成测试将有助于确保一切无缝运行。
自动化应该捕捉“所有”错误:当自动化测试针对一个新的特性分支运行时，如果它导致一个不相关的屏幕崩溃，那么这个错误就被标记为“回归”错误。自动化的目标是帮助找到这些错误，它不能完全取代手工测试。