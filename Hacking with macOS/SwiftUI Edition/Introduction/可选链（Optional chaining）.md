处理可选型有时可能感觉有一点儿笨手笨脚，而所有的解包及检查会变得过于繁琐，至于与你可能想扔下一些感叹号来强制解包，这样你就可以继续工作。然而，要小心：如果你强制解包一个没有值的可选型，你的代码会崩溃。

Swift 有两种技术可以帮助使你的代码不那么复杂。第一种叫做可选链，它允许仅当你的可选型有值时才运行代码。让我们开始吧，把下面的代码放进你的 playground 中：

```swift
func albumReleased(year: Int) -> String? {
  switch year {
  case 2006: return "Taylor Swift"
  case 2008: return "Fearless"

  case 2010: return "Speak Now"
  case 2012: return "Red"
  case 2014: return "1989"
  default: return nil
  } 
}

let album = albumReleased(year: 2006)
print("The album is \(album)")
```

![Pasted image 20240124133805.png](./attachments/Pasted%20image%2020240124133805.png)


那会在结果面板中输出“The album is Optional("Taylor Swift")“。

如果我们想要把 **albumReleased()** 的返回值转换成大写字母（也就是“TAYLOR SWIFT”而非”Taylor Swift“）我们可以调用那个字符串的 **uppercased()** 方法。例如：

```swift
let str = "Hello world"
print(str.uppercased())
```

![Pasted image 20240124134009.png](./attachments/Pasted%20image%2020240124134009.png)


这里的问题是，**albumReleased()** 返回一个可选的字符串：它可能返回一个字符串，它也可能什么都不返回。因此，我们真正想说的是，“如果我们拿回了一个字符串则大写它，否则什么都别做”。而这正是可选链登场的地方，因为它确实提供了那种行为。

试着把最后两行代码改成这样：

```swift
let album = albumReleased(year: 2006)?.uppercased()
print("The album is \(album)")
```

![Pasted image 20240124134233.png](./attachments/Pasted%20image%2020240124134233.png)


注意在这里有一个问号，即可选链：问号之后的一切仅在该问号前面有值时才会被运行。这不影响 **album** 的底层数据类型，因为那行代码现在要么返回 nil 要么会返回大写的专辑名——它仍然是个可选的字符串。

你需要多长的可选链都可以，例如：

```swift
let album = albumReleased(year:
2006)?.某些可选的值?.某些可选的值?.随便
```

Swift 会从左往右检查它们直到发现 nil，那时它会停止。

## 空值合并运算符（The nil coalescing operator）
空值合并运算符让你的代码更简单也更快，而且还有一个如此浮夸的、让很多人畏惧的名字。这实在是遗憾，因为如果你花时间把这个空值合并运算符搞明白，它会让你的生活变得更轻松！

它做的事情就是让你可以说“如果你可以的话使用值 A，但如果值 A 是 nil 则使用值 B“。就是这样。它在处理可选型时尤其有帮助，因为它有效地避免了它们是可选的，毕竟你提供了一个不可选的值 B。因此，如果 A 是可选的而且它有一个值，就使用它（我们有了一个值）。如果 A 存在当没有值，就使用 B（所以我们还是有一个值）。无论如何，我们肯定有一个值。

为了给你一个真实的情境，试着在你的 playground 中使用这段代码：

```swift
let album = albumReleased(year: 2006) ?? "unknown"
print("The album is \(album)")
```

那个双问号就是空值合并运算符，而在这种情况下它表示“如果 **albumReleased()** 返回了一个值就把它放进这个 **album** 变量，但如果 **albumReleased()** 返回 nil 就使用”unknown“代替”。

![Pasted image 20240124140154.png](./attachments/Pasted%20image%2020240124140154.png)


如果你现在看这个结果面板里面，会看到在那里打印了“The album is Taylor Swift”——不再有可选型了。这是因为 Swift 现在可以确保它会拿回一个真的值，无论是因为这个函数会返回一个，还是因为你提供了“unknown”。这反过来意味着你无需去解包任何东西或冒崩溃的风险：保证你真的有数据去处理，这让你的代码更安全而且更容易使用。