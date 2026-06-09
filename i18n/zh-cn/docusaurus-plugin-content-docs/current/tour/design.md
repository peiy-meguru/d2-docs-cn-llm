# 设计决策

import WebPImage from '@site/src/components/WebPImage';

以下是指引 D2 发展的设计决策。我们已尽力避免过去的错误，并从最成功的现代编程和配置语言中汲取灵感。

设计决策本质上意味着权衡取舍，其中一些你可能会不同意。但是，如果你是一名程序员，D2 为你而生，我们相信你会发现这些决策的集合构成了一门让你感到得心应手的语言。

随着语言的不断发展，这些决策也将不可避免地演变。

## 可读性 > 原型速度

可读性和原型速度都很重要，但当需要在两者之间做选择时，D2 通常更偏向可读性。

大多数时候，这并非二选一。好的编程语言特性通常会在两个方向上带来更高的收益。D2 的语法轻量且设计使得 autofmt 总能为你正确格式化，跨项目保持一致。

希望你能在易用性、原型速度和可读性之间找到良好的平衡，按此顺序。D2 特别避免的是抑制这三者的简洁紧凑语法。

例如，以下是定义圆柱体的两种方式。

D2：

```d2
A: Christmas {shape: cylinder}
```

Mermaid：

```
A[(Christmas)]
```

D2 的方式稍微不那么紧凑，但可读性大大提高。它也更容易编写，我的意思是，你不会忘记 cylinder（圆柱体）叫做 cylinder，但很容易忘记 `[(x)]` 表示圆柱体。

## 警告 > 错误

D2 会尽可能编译。例如，假设你应用了一个不存在的类（class），或添加了一个对特定形状（shape）无效的样式（style）。如果用户错误是 D2 可以忽略的，它会成功编译，最多给出警告。没有什么比在调试时注释掉一些代码，却得到一个关于未使用变量（variable）的停止世界的错误消息更烦人的了。

## 良好的默认值

默认、零定制的 D2 应该能生成良好的图表。这要求对什么构成良好的默认值有明确的看法。例如，D2 自带一个默认主题（theme）。而不是采用单色形状（shape）的开放式设计，令人愉悦的色彩成为默认。

## 针对桌面和服务端优化

D2 拥有强大的 CLI，内置监视模式，维护了 `man` 页面，并允许从 stdin 读取和输出到 stdout。图片和字体默认嵌入到图表中，因此导出的图表是独立的——在任何地方看起来都一样。D2 支持多种格式，如 PPT 和 GIF。它允许导入（import），因此你可以将图表模块化为多个文件。有一个语言 API 用于以编程方式编辑和编写 D2。所有这些都与用于浏览器渲染的 Web 库背道而驰。D2 计划发布并维护一个用于此目的的 Web 库，但功能集将有所精简，优先级次之。

## 单一用例：记录软件

D2 专注于为软件工程师记录软件提供价值。我们不是一个通用的可视化工具。其他语言可能支持思维导图、甘特图、桑基图、维恩图，甚至能够绘制美国地图。D2 不做这些，也不会支持这些。

在 D2 中，这些被认为是臃肿。将一种语言拉伸到覆盖如此大表面积的不同图表类型，实质上将其拆分为 DSL 内部的 N 个不同的小 DSL。当语法需要支持 N 种完全不同的图表类型时，它几乎无法发展。这与 DSL 的初衷相悖——即让子集任务更加方便。

## 设计系统，而非图表

D2 的目的是描述你正在记录的系统。语言应该在系统设计和图表设计之间做出清晰区分。

考虑在 Graphviz 图表中自定义样式需要什么：

```
digraph "Linux_kernel_diagram" {
	fontname="Helvetica,Arial,sans-serif"
	node [fontname="Helvetica,Arial,sans-serif"]
	edge [fontname="Helvetica,Arial,sans-serif"]
	graph [
		newrank = true,
		nodesep = 0.3,
		ranksep = 0.2,
		overlap = true,
		splines = false,
	]
	node [
		fixedsize = false,
		fontsize = 24,
		height = 1,
		shape = box,
		style = "filled,setlinewidth(5)",
		width = 2.2
	]
	edge [
		arrowhead = none,
		arrowsize = 0.5,
		labelfontname = "Ubuntu",
		weight = 10,
		style = "filled,setlinewidth(5)"
	]
```

想象一下，如果你无法分离 HTML 和 CSS，而必须全部内联。

当然，良好的美观性对于好的文档至关重要。D2 当然优先考虑美观性，但它必须与内容解耦。

D2 是唯一允许你仅定义节点和边，将所有样式（style）导入（import）到一个单独文件中，并可以切换该文件以获得不同美观效果的语言。

## 适配白板

虽然 "graph" 和 "diagram" 通常是可互换的术语，但就 D2 而言，diagram（图表）是一种可以放在大白板上的简化表示。在达到一定数量的节点和边之后，例如 1000 个节点，这种表示更像图论中的图，而不是软件架构图表。它们的用例不再是理解每个单独的 shape（形状）和 connection（连接），而是观察整体模式。D2 不是为这种用例设计的。有更好的工具可以做到这一点。


<WebPImage src={require('@site/static/img/screenshots/graph.png').default} webpSrc={require('@site/static/img/screenshots/graph.webp').default} width={300} alt="graph example"/>
