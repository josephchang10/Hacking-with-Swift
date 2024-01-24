你已经见过 **if** 语句，刚刚是循环，但 Swift 有另一种类型的流程控制叫做 **switch/case**。把这个看作 **if** 的一种高级形式是最容易的，因为你可以有很多匹配项而 Swift 会执行合适的那个。

在一个 **switch/case** 的最基本形式中，你告诉 Swift 你希望去检查什么变量，然后给那个变量提供一列可能的情况。Swift 会找到与你的变量的匹配的第一种情况，然后运行它的代码块。当那个块结束时，Swift 退出这整个 **switch/case** 块。

这是一个基本的例子：

```swift
let liveAlbums = 2

switch liveAlbums {
case 0:
  print("You're just starting out")

case 1:
  print("You just released iTunes Live From SoHo")

case 2:
  print("You just released Speak Now World Tour")

default:
  print("Have you done something new?")
}
```

![Pasted image 20240123100043.png](./attachments/Pasted%20image%2020240123100043.png)


我们完全可以使用很多 **if** 和 **else if** 块来写那段，但这种方式更加清晰，而这一点很重要。

**switch/else** 的一项优势是 Swift 会确保你的 cases 是穷尽的。那就是说，如果存在这样的可能性，你的变量拥有一个你没有检查的值，Xcode 会拒绝去构建你的 app。

在这些值最终是以开放式结尾的情况下，就像我们的整数 **liveAlbums**，你需要包含一个 **default** case 来捕获这些潜在的值。是的，哪怕你“知道”你的数据只能落在一个特定的区间内，Swift 还是希望万无一失。

Swift 可以对你的 case 语句应用一些求值以便与变量匹配。例如，如果你希望检查一个区间的可能值，你可以像这样使用闭区间运算符：

```swift
let studioAlbums = 5

switch studioAlbums {
case 0...1:
  print("You're just starting out")
  
case 2...3:
  print("You're a rising star")
  
case 4...5:
  print("You're world famous!")

default:
  print("Have you done something new?")
}
```

![Pasted image 20240123113942.png](./attachments/Pasted%20image%2020240123113942.png)


你应该知道的一件事是 Swift 中的 **switch/case** 块不会像其他语言一样穿透（fall through），你可能曾经见过这些语言。如果你习惯在你的 **case** 块中写 **break**，你要知道在 Swift 中这是不需要的。

而是使用 **fallthrough** 关键字来让一个 case 穿进下一个——恰恰相反。当然，如果你不知道这些意味着什么，就更好了：不用考虑它！