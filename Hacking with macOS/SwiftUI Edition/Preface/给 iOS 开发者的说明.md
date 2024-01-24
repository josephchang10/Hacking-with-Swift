SwiftUI apps for iOS 和 macOS 有广泛的共同点，但也有很多不同的东西——学着去识别那些明显的 “Mac” 功能是构建高品质 macOS apps 过程中的一部分。

你至少需要知道这些：

1. 这本书假设你之前不了解 macOS 开发，无论是 SwiftUI 还是别的——构建 apps 你需要知道的每件事都在这里教了，包括 Swift 的基础。
2. 如果你已经学习了 SwiftUI for iOS，你将能够非常快速地开始为 macOS 构建 SwiftUI apps——几乎所有核心视图和 modifiers 实际上都是完全相同的。
3. 如果已经完成了 100 Days of SwiftUI 或读过我的书 Hacking with iOS，你可以跳过这里的技巧项目因为尽管它们并非*完全相同*但非常相似，所以它们不会教你任何新东西——SwiftUI 在跨平台方面做的真的很棒。
4. 在少数地方我们需要去使用 AppKit 以完成 SwiftUI 做不了的事情，你会发现很多 “UI” 的东西有同等的 “NS”——例如，**UIImage** 变成了 **NSImage**。它们可能看起来类似，但通常这些类型的实现通常差别很大。
5. 在两个平台上 Swift 语言当然是完全相同的，但在 macOS 上运行的东西自然会更快，因为你用的是强大的多的硬件——64GB 或更多的 RAM 已是常态，而且有了 Apple Silicon CPUs ，你可能正在运行 20 核或更多的设备。
