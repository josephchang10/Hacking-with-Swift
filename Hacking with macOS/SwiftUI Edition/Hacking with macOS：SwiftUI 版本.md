通过真实 Swift 项目学习去制作桌面 apps

***Paul Hudson***

版本：2022-11-01

# 目录

## 前言
[关于此书](./Preface/%E5%85%B3%E4%BA%8E%E6%AD%A4%E4%B9%A6.md)

[给 iOS 开发者的说明](./Preface/%E7%BB%99%20iOS%20%E5%BC%80%E5%8F%91%E8%80%85%E7%9A%84%E8%AF%B4%E6%98%8E.md)

## [向完全的新手介绍 Swift](./Introduction/%E5%90%91%E5%AE%8C%E5%85%A8%E7%9A%84%E6%96%B0%E6%89%8B%E4%BB%8B%E7%BB%8D%20Swift.md)
[如何安装 Xcode 并创建 playground](./Introduction/%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%20Xcode%20%E5%B9%B6%E5%88%9B%E5%BB%BA%20playground.md)

[变量和常量](./Introduction/%E5%8F%98%E9%87%8F%E5%92%8C%E5%B8%B8%E9%87%8F.md)

[数据的类型](./Introduction/%E6%95%B0%E6%8D%AE%E7%9A%84%E7%B1%BB%E5%9E%8B.md)

[运算符](./Introduction/%E8%BF%90%E7%AE%97%E7%AC%A6.md)

[字符串插值（String Interpolation）](./Introduction/%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%8F%92%E5%80%BC%EF%BC%88String%20Interpolation%EF%BC%89.md)

[数组](./Introduction/%E6%95%B0%E7%BB%84.md)

[字典](./Introduction/%E5%AD%97%E5%85%B8.md)

[条件语句](./Introduction/%E6%9D%A1%E4%BB%B6%E8%AF%AD%E5%8F%A5.md)

[循环](./Introduction/%E5%BE%AA%E7%8E%AF.md)

[Switch case](./Introduction/Switch%20case.md)

[函数](./Introduction/%E5%87%BD%E6%95%B0.md)

[可选型（Optionals）](./Introduction/%E5%8F%AF%E9%80%89%E5%9E%8B%EF%BC%88Optionals%EF%BC%89.md)

[可选链（Optional chaining）](./Introduction/%E5%8F%AF%E9%80%89%E9%93%BE%EF%BC%88Optional%20chaining%EF%BC%89.md)

[枚举](./Introduction/%E6%9E%9A%E4%B8%BE.md)

[Structs（结构体）](./Introduction/Structs%EF%BC%88%E7%BB%93%E6%9E%84%E4%BD%93%EF%BC%89.md)

[类](./Introduction/%E7%B1%BB.md)

[属性](./Introduction/%E5%B1%9E%E6%80%A7.md)

[静态属性和方法](./Introduction/%E9%9D%99%E6%80%81%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95.md)

[访问控制](./Introduction/%E8%AE%BF%E9%97%AE%E6%8E%A7%E5%88%B6.md)

[多态和类型转换](./Introduction/%E5%A4%9A%E6%80%81%E5%92%8C%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2.md)

[闭包](./Introduction/%E9%97%AD%E5%8C%85.md)

[协议](./Introduction/%E5%8D%8F%E8%AE%AE.md)

[扩展](./Introduction/%E6%89%A9%E5%B1%95.md)

[协议扩展](./Introduction/%E5%8D%8F%E8%AE%AE%E6%89%A9%E5%B1%95.md)

[总结](./Introduction/%E6%80%BB%E7%BB%93.md)

## 项目 1：[风暴查看器](./Project%201/%E9%A3%8E%E6%9A%B4%E6%9F%A5%E7%9C%8B%E5%99%A8.md)
[风暴查看器：设置](./Project%201/%E9%A3%8E%E6%9A%B4%E6%9F%A5%E7%9C%8B%E5%99%A8%EF%BC%9A%E8%AE%BE%E7%BD%AE.md)

[使用视图](./Project%201/%E4%BD%BF%E7%94%A8%E8%A7%86%E5%9B%BE.md)

[介绍列表](./Project%201/%E4%BB%8B%E7%BB%8D%E5%88%97%E8%A1%A8.md)

[加载我们的图像](./Project%201/%E5%8A%A0%E8%BD%BD%E6%88%91%E4%BB%AC%E7%9A%84%E5%9B%BE%E5%83%8F.md)

[响应图像选择](./Project%201/%E5%93%8D%E5%BA%94%E5%9B%BE%E5%83%8F%E9%80%89%E6%8B%A9.md)

[最终润色](./Project%201/%E6%9C%80%E7%BB%88%E6%B6%A6%E8%89%B2.md)

[风暴查看器：总结](./Project%201/%E9%A3%8E%E6%9A%B4%E6%9F%A5%E7%9C%8B%E5%99%A8%EF%BC%9A%E6%80%BB%E7%BB%93.md)

## 项目 2：Cows and Bulls
Cows and Bulls：设置

设计我们的用户界面

列表中的填充

Marking guesses

额外改进

自定义这个游戏

Now take a bow!

Cows and Bulls：总结

## 项目 3：Views and Modifiers
Views and modifiers：介绍

为何 SwiftUI 的视图使用结构体？

为何 modifier 的顺序有影响

为何 SwiftUI 的视图类型使用 ”some View“？

Conditional modifiers

Environment modifiers

Views as properties

视图组合

自定义 modifiers

自定义容器

Views and modifiers：总结

## 项目 4：文字解释器
文字解释器：介绍
Bootstrapping an app
执行语义分析
查找替代单词
检测名字和语言
引入一个外部包
Flags and options
文字解释器：总结

## 项目 5：MultiMap
MultiMap：介绍
创建一张交互式地图
搜索位置
处理列表多选
切换至 searchable()
最终改进
MultiMap：总结

## 项目 6：动画
动画：介绍
创建隐式动画
自定义 SwiftUI 中的动画
动画绑定
创建显示动画
控制动画栈
手势动画
用过度显示和隐藏视图
使用 ViewModifier 构建自定义过度
动画：总结

## 项目 7：Fast Track
Fast Track：设置
从列表到网格
从一台服务器下载数据
远程图像和自定义子视图
播放音频
添加一些额外改进
Fast Track：总结

## 项目 8：Odd One Out
Odd One Out：设置
创建一网格的按钮
生成布局
点击去赢
游戏结束
Odd One Out：总结

## 项目 9：绘图
绘图：介绍
通过 SwiftUI 创建自定义路径
SwiftUI 中的路径 vs 形状
通过 InsettableShape 添加 strokeBorder() 支持
使用 CGAffineTransform 和甚至更古怪的填充转变形状
使用 ImagePaint 的创意边框和填充
通过 drawingGroup() 启用高性能 Metal 渲染
SwiftUI 中的特殊效果：模糊、blending 等等
通过 animatableData 动画简单的形状
通过 AnimatablePair 动画复杂的形状
通过 SwiftUI 创建一个呼吸描记器
绘图：总结

## 项目 10：Time Buddy
Time Buddy：设置
空的艺术
你好，菜单栏
到 SwiftUI
动态菜单项目
Time Buddy：总结

## 项目 11：Bubble Trouble
Bubble Trouble：设置
清理 Xcode 模板
气泡……到处都是气泡！
Setting the universe in motion
添加一些难度
Gotta pop ‘em all
Bubble Trouble: 总结

## 项目 12：布局和 Geometry
布局和 geometry：介绍
SwiftUI 中的布局是如何工作的
对齐和 alignment guide
如何创建一个自定义的 alignment guide
SwiftUI 视图的绝对位置
理解 GeometryReader 中的 frames 和 coordinates
使用 GeometryReader 的 ScrollView 效果
布局和 geometry：总结

## 项目 13：Screenable
Screenable：设置
介绍 FileDocument
通过 Canvas 自定义渲染
从你的 app bundle 加载文件
通过拖放添加图像
颜色和渐变
添加阴影
导出完成的产品
Screenable：总结

## 项目 14：Shooting Gallery
Shooting Gallery：设置
创建游戏世界
创建一个自定义 node
Click, click, bang!
添加一些改进
Shooting Gallery：总结

## 项目 15：可访问性
可访问性：介绍
通过实用的标签识别视图
隐藏和分组可访问性数据
读取控件的值
可访问性：总结

## 项目 16：书虫
书虫：设置
实体和属性
获取和创建数据
观察外部对象
添加一些最终改进
书虫：总结

## 项目 17：Match Tree
Match Tree：设置
一网格的球
匹配颜色
腾出更多空间
一缕烟
Match Tree：总结

## 项目 18：Core Data
Core Data：介绍
创建 NSManagedObject 子类
使用约束确保 Core Data 对象是唯一的
使用 NSPredicate 过滤 @FetchRequest
Core Data、SwiftUI 和 @FetchRequest 的一对多关系
Core Data：总结
