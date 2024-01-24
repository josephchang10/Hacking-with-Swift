Structs 是复合（complex）数据类型，意味着它们由多个值组成。你创建一个 struct 的实例并填入它的值，然后你可以将其作为单一值在你的代码中到处传递。例如，我们可以定义一个 **Person** struct 类型，包含两个属性（properties）：**clothes** 和 **shoes**：

```swift
struct Person {
  var clothes: String
  var shoes: String
}
```

当你定义一个 struct 时，Swift 使它们非常容易创建，因为它自动生成一个所谓的成员逐一初始化器（memberwise initializer）。通俗来说，它表示通过传入它的两个属性的初始值来创建该 struct，像这样：

```swift
let taylor = Person(clothes: "T-shirts", shoes: "sneakers")
let other = Person(clothes: "short skirts", shoes: "high
heels")
```

![Pasted image 20240124183338.png](./attachments/Pasted%20image%2020240124183338.png)


一旦你创建好了一个 struct 的实例，你可以读取它的属性，通过直接写这个 struct 的名字、一个点以及你希望读取的属性：

```swift
print(taylor.clothes)
print(other.shoes)
```

![Pasted image 20240124183524.png](./attachments/Pasted%20image%2020240124183524.png)


如果你把一个 struct 分配给另一个，Swift 会在幕后拷贝它，使其成为一个完整、独立的副本。不过，这话说的不完全准确：Swift 使用了一项叫做“写入时拷贝（copy on write）”的技术，也就是说仅在你尝试去修改它时才会真正拷贝你的数据。

为了帮你理解 struct 的拷贝是如何工作的，把这些放进你的 playground 里：

```swift
struct Person {
  var clothes: String
  var shoes: String

}

let taylor = Person(clothes: "T-shirts", shoes: "sneakers")
let other = Person(clothes: "short skirts", shoes: "high
heels")

var taylorCopy = taylor
taylorCopy.shoes = "flip flops"	

print(taylor)
print(taylorCopy)				   
```

![Pasted image 20240124184150.png](./attachments/Pasted%20image%2020240124184150.png)


这创建了两个 **Person** structs，然后又创建了第三个，叫做 **taylorCopy**，作为 **taylor** 的一份拷贝。接下来的部分比较有趣：代码改变了 **taylorCopy**，然后同时打印了它和 **taylor**。如果你查看你的结果面板（你可能需要调整大小以显示完整）你会发现这份拷贝的值和原始的不同：改变一个并不会改变另一个。

## structs 内部函数
你可以把函数放在 structs 内部，实际上对于所有在 struct 内部读取或写入数据的函数来说，这样做是个好主意。例如，我们可以给我们的 **Person** struct 加一个函数来描述他们穿的是什么，像这样：

```swift
struct Person {
  var clothes: String
  var shoes: String

  func describe() {
    print("I like wearing \(clothes) with \(shoes)")
  } 
}
```

![Pasted image 20240124215119.png](./attachments/Pasted%20image%2020240124215119.png)


还有一件你应该知道、但从那段代码里看不出来的事：当你在 struct 内部编写一个函数时，它被改称为一个*方法（method）*。在 Swift 中无论是一个函数还是一个方法你都用 **func** 来写，但在谈论它们时这个差别仍然存在。