---
pagination_next: tour/dagre
---
import CodeBlock from '@theme/CodeBlock';
import WebPImage from '@site/src/components/WebPImage';
import DirectionRight from '@site/static/d2/direction-right.d2';
import DirectionUp from '@site/static/d2/direction-up.d2';

# 概述

D2 支持使用多种不同的布局引擎。布局引擎的选择会显著影响你的整体图表。每种布局对某些关键字的支持程度也不同。尽管我们尽最大努力保持一致性，但最终我们对自定义构建的布局引擎拥有最大的控制权，而其他布局引擎的支持则有所限制。

## 布局引擎

- [dagre](/tour/dagre/)（默认）：一种快速的有向图布局引擎，生成分层/层次化布局。基于 Graphviz 的 DOT 算法。
- [ELK](/tour/elk/)：也是一种有向图布局引擎。比 dagre 更成熟，维护更好（由兼职学术研究团队开发），有持续的新版本发布。
- [TALA](/tour/tala/)：专为软件架构图设计的新型布局引擎。

你可以选择你喜欢的、最适合当前图表的布局引擎。每种引擎都有其权衡，请访问各个页面了解更多信息。

要查看你机器上可用的布局，可以运行 `d2 layout`。每个布局引擎还可以设置特定的可配置标志，你可以通过运行 `d2 layout [engine]` 查看，例如 `d2 layout dagre`。

要指定使用的布局，可以设置 `--layout=dagre` 标志，或将其设置为环境变量 `$D2_LAYOUT=dagre`。

### 布局特定功能

某些关键字和功能仅适用于特定的布局引擎。我们编写并维护了 TALA，因此它是我们唯一拥有完全控制权的布局引擎。我们为 Dagre 和 ELK 编写了 shim，但有些东西是布局引擎的根本特性，要完全支持所有功能，只能 fork（我们最终可能会这样做）。

这些内容在文档的其他部分也有提及，以下汇集于此：

- `near` 设置为另一个对象。`near` 可以在所有布局引擎中设置为常量，但只有 TALA 可以将其设置为对象。
- 容器上的 `width` 和 `height`。TALA 将很快添加此功能，但目前仅 ELK 支持。请注意，这些关键字在所有布局引擎中都适用于非容器。
- `top` 和 `left` 锁定位置仅适用于 TALA。
- 从祖先到后代的连接（例如容器到其子元素）在 Dagre 中不支持。

## 方向（Direction）

设置 `direction` 为以下值之一，来控制图表的明确流向。

:::info 选项
- `up`
- `down`
- `right`
- `left`
:::

<CodeBlock className="language-d2">
    {DirectionRight}
</CodeBlock>

<div
className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/direction-right.svg2')}}></div>

<CodeBlock className="language-d2">
    {DirectionUp}
</CodeBlock>

<div
className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/direction-up.svg2')}}></div>

### 每个容器的方向（仅 TALA）

:::info
除 TALA 外，所有布局引擎只能在全局级别设置方向。这是它们算法的一个限制——它们是层次化的，只能在一个方向上工作。我们正在研究使其工作的方法。
:::

```d2
vars: {
  d2-config: {
    layout-engine: tala
  }
}
direction: down
a -> b -> c

b: {
  direction: right
  1 -> 2 -> 3
}

a: {
  direction: left
  foo -> bar
}
```

<WebPImage src={require('@site/static/img/screenshots/tala-direction.png').default} webpSrc={require('@site/static/img/screenshots/tala-direction.webp').default} alt="directions in TALA" />
