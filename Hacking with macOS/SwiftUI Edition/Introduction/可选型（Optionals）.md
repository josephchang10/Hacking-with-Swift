Swift 是一门非常安全的语言，这意味着它努力地保证你的代码永远不会以意外的方式失败。

代码最常见的失败方式之一是在它尝试去使用坏的或缺失的数据时。例如，想象一个像这样的函数：

```swift
func getHaterStatus() -> String {
  return "Hate"								 
}
```

那个函数不接受任何参数，而且它返回一个字符串：“Hate”。但如果今天是一个特别阳光的日子，而那些黑子（haters）并不想黑——然后怎么办呢？好吧，可能我们不想返回任何东西：这位黑子今天什么也不黑。

现在说到字符串，你可能认为一个空字符串是表达没有任何东西的好方法，有时确实如此。但数字呢——0 是一个“空数字”吗？还是 -1？

你在开始尝试给自己设定虚构的规则之前，Swift 提供了一个解决方案：可选型。一个可选值可能有值，也可能没有值。大部分人感觉可选型不好理解，这很正常——我会尝试以几种方式来解释它，但愿会有一种有效。

现在，想象一份有调查问卷，你问某个人，“从 1 分到 5 分，Taylor Swift 有多赞？”——如果某个人从未听说过她，他该回答什么呢？1 分会不公平地贬低她，而 5 分则是在他们不知道 Taylor Swift 是谁的情况下赞美她。这里的解决方案是可选型：“我不想提供任何数字。”

当我们使用 **-> String** 时，意味着“这里肯定会返回一个字符串”，也就是说这个函数*不能*不返回值，因此知道你总是会拿回一个你可以用作一个字符串的值，这可以被称作安全。如果我们希望告诉 Swift 这个函数可能返回一个值，但也可能不会，我们需要用这个代替：

```swift
func getHaterStatus() -> String? {
  return "Hate"								  
}
```

注意那个多的问号：**String?** 代表“可选的字符串”。现在，在我们的例子中不管怎样我们仍然在返回“Hate”，但让我们继续并进一步修改那个函数：如果天气（weather）是阳光的（sunny），这些黑子们已经改过自新并放弃了他们黑子的生活，因此我们希望返回空值。在 Swift 中，这个“空值”有一个特殊的名称：**nil**。

把这个函数改成这样：

```swift
func getHaterStatus(weather: String) -> String? {
  if weather == "sunny" {
    return nil
  } else {
    return "Hate"
  }
}
```

这接收了一个字符串参数（weather）并返回一个字符串（黑子状态（hating status）），但那个返回值可能存在也可能不存在——它是 nil。在这个例子中，意味着我们可能获得一个字符串，也可能获得 nil。

![Pasted image 20240124104605.png](./attachments/Pasted%20image%2020240124104605.png)


现在是重点：Swift 希望你的代码是真正安全的，而试图是用一个 nil 值是一个不好的想法。它可能会让你的代码崩溃，它可能会导致你的 app 逻辑出现问题，或者它可能让你的用户界面显示错误的东西。因此，在你将一个值声明为可选型的时候，Swift 会确保你安全地处理它了。

让我们现在试试这个：添加这几行代码到你的 playground：

```swift
var status: Stirng
status = getHaterStatus(weather: "rainy")
```

这第一行创建了一个字符串变量，而第二行把来自 **getHaterStatus()** 的值分配给它——而今天的天气是多雨（rainy），所以这些黑子们当然在黑啦。

那段代码不会运行，因为我们说了那个 **status** 是 **String** 类型，它需要一个值，但 **getHaterStatus()** 可能不会提供，因为它返回了一个可选的字符串。也就是说，我们说的是在 **status** 那里*肯定*会有一个字符串，但 **getHatersStatus()** 可能什么都不返回。Swift 根本不会让你犯这个错误，这极为有帮助，因为它有效阻止了一整类常见的 bugs。

![Pasted image 20240124111748.png](./attachments/Pasted%20image%2020240124111748.png)


要修复这个问题，我们需要让这个 **status** 变量是一个 **String?**，或者直接整个去掉类型注释并让 Swift 是用类型推断。第一个选项看起来像这样：

```swift
var status: String?
status = getHaterStatus(weather: "rainy")
```

而第二个像这样：

```swift
var status = getHaterStatus(weather: "rainy")
```

无论你选的哪种，那个值可能存在也可能不存在，而 Swift 默认不会让你以危险的方式使用它。作为一个例子，想像一个像这样的函数：

```swift
func takeHaterAction(status: String) {
  if status == "Hate" {
      print("Hating")
  }
}
```

这接收一个字符串并根据它的内容打印一条消息。这个函数接收一个 **String** 值，而*不是*一个 **String?** 值——这里你不能传入一个可选型，它想要一个实打实的字符串，这意味着我们不能用我们制作的这个 **status** 变量调用它。

Swift 有两种解决方案。两种都在使用，但其中一种相比另一种是绝对更受欢迎的。第一种叫做方案叫做可选型解包（unwrapping），而它是使用特殊语法在一个条件语句内部完成的。它同时做两件事：检查一个可选型是否有值，而如果有的话就把它解包为一个非可选的类型，然后运行一个代码块。

这个语法看起来像这样：

```swift
if let unwrappedStatus = status {
  // unwrappedStatus 包含一个不可选的值！
} else {
  // 如果你想要一个 else 块，在这儿……
}
```

这些 **if let** 语句在一行简明的代码中检查并解包，这让他们非常常用。使用这个方法，我们可以安全地解包 **getHaterStatus()** 的返回值并确保我们仅通过一个有效的、非可选的字符串调用 **takehaterAction()**。这是完整的代码：

```swift
func getHaterStatus(weather: String) -> String? {
  if weather == "sunny" {
    return nil
  } else {
    return "Hate"
  }
}

func takeHaterAction(status: String) {
  if status == "Hate" {
    print("Hating")
  }
}

if let haterStatus = getHaterStatus(weather: "rainy") {
  takeHaterAction(status: haterStatus)
}
```

![Pasted image 20240124113459.png](./attachments/Pasted%20image%2020240124113459.png)


**如果你理解了这个概念，请往下跳到写着“强制解包可选型”的标题处。** 如果你还是对可选型不太有把握，继续阅读。

好吧，如果你还在这里，就表示上面的解释要么没有意义，要么是你有点儿理解了，但大概还要一些说明。可选型在 Swift 中被广泛使用，因此你确实真的需要去理解它们。我会试着再解释一遍，以另一种方式，但愿这会有帮助！

这是一个新函数：

```swift
func yearAlbumReleased(name: String) -> Int {
  if name == "Taylor Swift" { return 2006 }
  if name == "Fearless" { return 2008 }
  if name == "Speak Now" { return 2010 }
  if name == "Red" { return 2012 }
  if name == "1989" { return 2014 }

  return 0 
}
```

这接收一张 Taylor Swift 的专辑名称，并返回它被发布的年份。但如果我们用专辑名“Lantern”调用它，由于我们搞混了 Taylor Swift 和 Hudson Mohawke（很容易搞错，对吧？）那么它会返回 0 因为这不是 Taylor 的专辑之一。

![Pasted image 20240124114318.png](./attachments/Pasted%20image%2020240124114318.png)


但这里的 0 有意义吗？当然，如果专辑是在过去的公元 0 年发布的，那时 Caesar Augustus 是罗马的皇帝，0 可能有意义，但在这里它只是让人困惑——人们需要提前知道，0 意味着“未被识别”。

一个好的多的主意是重写那个函数以便它要么返回一个整数（在找到一个年份时）要么是 nil（在没找到时），这很简单，多亏了可选型。这是新的函数：

```swift
func yearAlbumReleased(name: String) -> Int? {
  if name == "Taylor Swift" { return 2006 }
  if name == "Fearless" { return 2008 }
  if name == "Speak Now" { return 2010 }
  if name == "Red" { return 2012 }
  if name == "1989" { return 2014 }

  return nil 
}
```

![Pasted image 20240124114911.png](./attachments/Pasted%20image%2020240124114911.png)


现在既然它返回 nil，我们需要去使用 **if let** 解包这个结果，因为我们需要去检查是否存在一个值。

**如果你现在理解了这个概念，请往下跳到写着“强制解包可选型”的标题处。** 如果你还是对可选型不太有把握，继续阅读。

好吧，如果你还在这里就说明你在可选型方面真的遇到了困难，因此我会最后解释它们一遍。

这是一个名字的数组：

```swift
var items = ["James", "John", "Sally"]
```

如果我们希望写一个函数，它在那个数组中查找并告诉我们一个特定名字的索引，我们可能会写一个类似这样的：

```swift
func position(of string: String, in array: [String]) -> Int {
  for i in 0..<array.count {
    if array[i] == string {
      return i
    } 
  }

  return 0 
}
```

那个循环遍历了这个数组中的所有项目，如果找到了一个匹配的就返回它的位置，否则返回 0.

现在试着运行这四行代码：

```swift
let jamesPosition = position(of: "James", in: items)
let johnPosition = position(of: "John", in: items)
let sallyPosition = position(of: "Sally", in: items)
let bobPosition = position(of: "Bob", in: items)
```

![Pasted image 20240124120010.png](./attachments/Pasted%20image%2020240124120010.png)


那会输出 0、1、2、0——James 和 Bob 的位置是相同的，尽管一个存在而另一个不存在。这是因为我用了 0 来表示“没找到”。简单的解决方法可能是让没找到是-1，但无论它是 0 还是-1 还是会有一个问题，因为你需要去记住那个特定的数字代表“没找到”。

解决方法是可选型：如果你找到了匹配的就返回一个整数，否则是 nil。事实上，这正是内置的“在数组中查找”方法使用的方式：**someArray.firstIndex(of: someValue)。**

![Pasted image 20240124120607.png](./attachments/Pasted%20image%2020240124120607.png)


当你处理这些“可能存在或不存在”的值时，Swift 会强制你在使用它们之前进行解包，从而确认这里可能没有值。这就是 **if let** 语法做的事情：如果该可选型有一个值，就解包并使用它，否则根本不使用它。你不会意外地使用一个可能为空的值，因为 Swift 不允许。

如果你*仍然*不确定如何使用可选型，那最好在 Twitter 上问我，而我会尝试提供帮助：你可以在 **@twostraws** 找到我。

## 强制解包可选型
Swift 允许你通过使用感叹号：**!** 从而凌驾于其安全性之上。如果你知道一个可选型绝对有值，你可以通过在它后面放上这个感叹号来强制解包它。

**然而，请注意：如果你在一个没有值的变量上这样尝试，你的代码会崩溃。**

为了拼凑出一个实例，这是一些基本代码：

```swift
func yearAlbumReleased(name: String) -> Int? {
  if name == "Taylor Swift" { return 2006 }
 . if name == "Fearless" { return 2008 }
  if name == "Speak Now" { return 2010 }
  if name == "Red" { return 2012 }
  if name == "1989" { return 2014 }

  return nil 
}

var year = yearAlbumReleased(name: "Red")

if year == nil {
  print("There was an error")
} else {
  print("It was released in \(year)")
}
```

这获得了一张专辑的发布年份。如果找不到这张专辑，**year** 会被设置为 nil，而且会打印一条错误消息。否则，会打印该年份。

但它真的会吗？好吧，**yearAlbumReleased()** 返回一个可选的整数，而这个代码没有使用 **if else** 来解包那个可选型。因此，它会如下打印：“It was released in Optional(2012)“——大概不是我们想要的！

![Pasted image 20240124122113.png](./attachments/Pasted%20image%2020240124122113.png)


此时在代码中已经检查过，我们有一个有效的值，因此这里再用一个 **if let** 来安全地解包这个可选型有点儿浪费时间。因此，Swift 提供了一种解决方案——把第二个 **print()** 调用改成这样：

```swift
print("It was released in \(year!)")
```

![Pasted image 20240124122509.png](./attachments/Pasted%20image%2020240124122509.png)


注意这个感叹号：它表示“我确定这包含一个值，因此现在强制解包它”。

通常来说强制解包可选型是不被推崇的——如果你发现自己在频繁这么干你可能要重新思考你的方式。

## 隐式解包可选型
你也可以使用这个感叹号语法来创建隐式解包的可选型，这是一些人真正感到困惑的地方。所以，请仔细阅读这里！

* 一个常规变量必需包含一个值。例如：**String** 必需包含一个字符串，即使那个字符串是空的，即 **""**。它*不能*是 nil。
* 一个*可选型*变量可能包含一个值，也可能不包含。它在被使用前必需被解包。例如：**String?** 可能包含一个字符串，或者它可能包含 nil。查明的唯一方式是去解包它。
* 一个隐式解包的可选型可能包含一个值，或者不包含，但它在被使用前*不*需要被解包。Swift 不会为你检查，因此你需要额外小心了。例如：**String!** 可能包含一个字符串，它也可能包含 nil——由你来判断以正确地使用它。它像一个常规的可选型，但 Swift 允许你不用解包的安全措施而直接访问值。如果你尝试这样做，就表示你知道这里存在一个值——但如果你错了你的 app 会崩溃。

![Pasted image 20240124124727.png](./attachments/Pasted%20image%2020240124124727.png)


你经常会遇到隐式解包的可选型的时刻，就是在你使用 iOS 上的 UIKit 或 macOS 上的 AppKit 处理用户界面的元素时。这些需要提前被声明，但在它们被创建之前你不能使用它们——而 Apple 喜欢在最后一刻创建用户界面元素以避免任何不必要的工作。你肯定知道需要持续解包值会很烦人，因此这些已经被隐式解包了。

如果你发现隐式解包有点儿难以理解，别担心——随着你对这门语言的使用，它会变得清晰起来，而且你会乐于知道在 SwiftUI 项目中它们很少见。

