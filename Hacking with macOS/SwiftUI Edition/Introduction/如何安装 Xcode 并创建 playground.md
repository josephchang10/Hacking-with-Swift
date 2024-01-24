Xcode 是 Apple 给开发者的编程应用程序。它在 Mac App Store 中是免费的，而且为 Apple 的平台做开发它是必需的。因此，你的第一项操作是**点击这里从 Mac App Store 安装 Xcode**——它的下载相当大，因此现在开始下载它然后继续阅读。

处于下载中时，我可以为你解释几个绝对的基础：

* **iOS** 是在所有 iPhones 和 iPads 上运行的操作系统的名称。它负责手机的所有基本操作，例如打电话、在屏幕上绘制以及运行 apps。
* **macOS** 是 Apple 的桌面操作系统的名称，它是 iOS、tvOS 甚至 watchOS 的技术先驱。
* **watchOS** 是 Apple 最小的操作系统的名称，复杂运行原生 apps 以及传送来自手机的通知。
* **tvOS** 是从 iOS 拆出来的以便在连接到 Apple TV 设备的电视上运行。
* **Swift** 是 Apple 的现代编程语言，允许你为 iOS、macOS 及其他平台编写 apps。它包含构建程序的功能，但不负责诸如用户界面、音频或网络之类的事情。
* **UIKit** 是 Apple 的原生用户界面工具集。它包含诸如按钮、文本框、导航控件等东西，而你使用 Swift 驱动它。
* **AppKit** 是 Apple 给 macOS 的原生用户界面工具集。和 UIKit 一样包含如按钮、文本框等东西，但专注在 macOS 上而非 iOS。
* **WatchKit** 是 Apple 在 SwiftUI 发布前给 watchOS 的原生用户界面工具集。虽然 UIKit 和 AppKit 有很多共同点，WatchKit 是显著不同的——而且简单的多。
* **SwiftUI** 是一个跨平台工具集，允许你为 iOS、macOS、tvOS 和 watchOS 构建 apps。
* **Cocoa Touch** 这个名称通常被用于 Apple 给 iOS 的庞大的框架集合。它包含做用户界面的 UIKit，但大部分人会说它也包含用于做 2D 游戏的 SpriteKit、做 3D 游戏的 SceneKit、给地图的 MapKit、用于绘图的 Core Graphics、用于动画的 Core Animation 等更多。
* **Cocoa** 这个名称用于 Apple 在 macOS 上的框架集合。严格来说它由给用户界面的 AppKit、用于基本功能的 Foundation 以及用于对象图的 Core Data 组成，但和 Cocoa Touch 一样它通常被用于表示“所有 macOS 开发”。
* **NeXTSTEP** 是一个由 Steve Jobs 创办的叫做 NeXT 的公司创造的操作系统。它被 Apple 收购了，于是 Jobs 重新掌控了这间公司，并且把 NeXTSTEP 科技直接放入了 Apple 的开发平台的核心。
* **模拟器（Simulator）** 是 Xcode 带的一项工具，外观和运行和一台真实的 iPhone、iPad、Apple TV 或 Apple Watch 几乎完全一致。它允许你非常快速地测试 apps，无需使用一台真实的设备。
* **Playgrounds** 是微型的 Swift 测试环境，允许你键入代码并立即查看结果。你不会用它们构建真实的 apps，但它们对于学习是绝佳的。我们会在这篇介绍中使用 playgrounds。
* **崩溃（Crashes）** 是指当你的代码发生灾难性错误并且你的 app 无法恢复时。如果一位用户在运行你的 app，它会直接消失而他们会回到主屏幕上。如果你正在 Xcode 中运行，你会看到一份崩溃报告。
* **Taylor Swift** 和 Swift 编程语言没有关系。你可能会认为这是个遗憾，但我会尝试在这个教程中使用她的歌来弥补这个不足。接受挑战。


这些就是基础了——如果 Xcode 还没有下载完，那么何不在等待时看一些 Taylor Swift 的视频？这本教程中的例子肯定会更有意义……

**安装好了 Xcode？好！让我们干起来吧……**

## 介绍 Swift playgrounds
当你启动 Xcode 时，你会看到这个 Welcome to Xcode 窗口，你可以在那里创建一个新项目或打开一个你最近的项目。我们目前不想要一个项目，因为我们会使用一个 *playground*——小型迷你项目，让我们快速运行代码。你可以前往 File 菜单并选择 New > Playground 搞一个新的 playground。

![Pasted image 20240122083111.png](./attachments/Pasted%20image%2020240122083111.png)


Xcode 会问你是希望为 iOS 还是 macOS 创建一个 playground，但这里无所谓——这篇介绍几乎仅与 Swift 语言有关，没有用户界面组件。为了避免问题，保留 platform 选中的 “iOS”。你会看到一列 playground 模板，你可以从中选择，但我们会这里会从小处着手因此请选择 Blank。

![Pasted image 20240122083545.png](./attachments/Pasted%20image%2020240122083545.png)


最后，Xcode 会要求你命名你的 playground——默认名称 “MyPlayground” 挺好，所以继续并点击 Create。

你会看到一个窗口一分为二。在左边你会看到这些：

```swift
import UIKit

var greeting = "Hello, playground"
```

而在右边，一旦 Xcode 构建并运行了代码，你会看到这个：“Hello, playground". 注意首次构建并运行这些代码会花大约 10 秒，但之后就快了——Xcode 需要在幕后启动一个迷你模拟器。

这个分屏很重要，因为它分开了代码和结果。代码在左边，而后面你会编辑这里来做你自己的 Swift 工作。结果在右边，而它为你显示你的 Swift 代码做了什么。在这个例子中，它在告诉我们我们成功设置了值 ”Hello, playground."

![Pasted image 20240122084211.png](./attachments/Pasted%20image%2020240122084211.png)


Playgrounds 会运行任何你写的代码，一次一行，并在边栏中显示更新的结果。每一行代码左侧你会看到一个蓝条，而如果你在那儿的各行上悬停你会发现你可以点击一个播放按钮以运行到那个点为止的代码。

Playgrounds 是尝试一些代码并快速查看结果的绝佳方式。它们也极为强大，你大约会在下面一小时里发现。让我们开始编写 Swift 吧！
