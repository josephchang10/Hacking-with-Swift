这是个花哨的名称，给一件实际上非常简单的事情：在一个字符串内部组合变量和变量。

清除所有你刚刚写的代码，只留下这行：

```swift
var name = "Tim McGraw"
```

如果你想为用户打印一条包含他们的名字的消息，正是字符串插值让这简单：你只要写一个反斜杠，然后一个开括号，然后你的代码，然后一个闭括号，像这样：

```swift
var name = "Tim McGraw"
"Your name is \(name)"
```

![Pasted image 20240122125808.png](./attachments/Pasted%20image%2020240122125808.png)


结果面板现在会显示“Your name is Tim McGraw”全部为一个字符串，因为字符串插值为我们组合了两者。

然而，我们本可以用 **+** 运算符写那一句，像这样：

```swift
var name = "Tim McGraw"
"Your name is " + name
```

![Pasted image 20240122130050.png](./attachments/Pasted%20image%2020240122130050.png)


……但那不不够高效，尤其是如果你在把多个变量组合起来时。此外，Swift 中的字符串插值足够智能，可以自动处理各种不同的数据类型。例如：

```swift
var name = "Tim McGraw"
var age = 25
var latitude = 36.166667

"Your name is \(name), your age is \(age), and your latitude is
\(latitude)"
```

![Pasted image 20240122130232.png](./attachments/Pasted%20image%2020240122130232.png)


用 **+** 做这些要困难得多，因为 Swift 不允许你把整数和 doubles 加到一个字符串。

此时你的结果可能在这个结果面板中放不下了，因此要么改变你的窗口大小要么悬停在结果上并点击显示的 + 按钮以在行内显示它。

字符串插值的强大功能之一是 **\\(** 和 **)** 中的东西实际上可以是一句完整的 Swift 表达式。例如，你在使用运算符在这里做算数，像这样：

```swift
var age = 25
"You are \(age) years old. In another \(age) years you will be
\(age * 2)."
```

![Pasted image 20240122130850.png](./attachments/Pasted%20image%2020240122130850.png)
