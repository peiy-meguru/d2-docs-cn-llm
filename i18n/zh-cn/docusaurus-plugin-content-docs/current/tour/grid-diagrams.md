import CodeBlock from '@theme/CodeBlock';
import Grid from '@site/static/d2/grid.d2';
import Grid2 from '@site/static/d2/grid-2.d2';
import Grid3 from '@site/static/d2/grid-3.d2';
import Grid4 from '@site/static/d2/grid-4.d2';
import GridDimensions from '@site/static/d2/grid-dimensions.d2';
import GridFill from '@site/static/d2/grid-fill.d2';
import GridNestedGrid from '@site/static/d2/grid-nested-grid.d2';
import Table from '@site/static/d2/table.d2';
import GridUnaligned from '@site/static/d2/grid-unaligned.d2';
import GridAligned from '@site/static/d2/grid-aligned.d2';
import GridPadding1 from '@site/static/d2/grid-padding-1.d2';
import GridPadding2 from '@site/static/d2/grid-padding-2.d2';
import MdTable from '@site/static/d2/md-table.d2';

# 网格图（Grid Diagrams）

网格图让你在结构化的网格中显示对象。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid.svg2')}}></div>

<CodeBlock className="language-d2" expandeable={true}>
    {Grid}
</CodeBlock>

两个关键字实现了这一切：
- `grid-rows`
- `grid-columns`

仅设置 `grid-rows`：

<CodeBlock className="language-d2">
    {Grid2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-2.svg2')}}></div>

仅设置 `grid-columns`：

<CodeBlock className="language-d2">
    {Grid3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-3.svg2')}}></div>

同时设置 `grid-rows` 和 `grid-columns`：

<CodeBlock className="language-d2">
    {Grid4}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-4.svg2')}}></div>

## 宽度和高度

要创建特定的结构，请使用 `width` 和/或 `height`。

<CodeBlock className="language-d2">
    {GridDimensions}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-dimensions.svg2')}}></div>

注意对象在每一行中均匀分布。

## 单元格扩展填充

当你只定义行或列之一时，对象会扩展填充。

<CodeBlock className="language-d2">
    {GridFill}
</CodeBlock>

注意 `Voters` 和 `Non-voters` 填充了空间。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-fill.svg2')}}></div>

## 主导方向

当你同时应用行和列时，先出现的定义是主导方向。主导方向是单元格被填充的顺序。

例如：

```d2-incomplete
grid-rows: 4
grid-columns: 2
# 一堆形状
```

由于 `grid-rows` 先定义，对象会先填充行，然后进入列。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-row-dominant.svg2')}}></div>

但如果反过来：

```d2-incomplete
grid-columns: 2
grid-rows: 4
# 一堆形状
```

则效果相反。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-column-dominant.svg2')}}></div>

:::info
这些动画也是纯 D2 制作的，因此你可以对网格图的构建过程进行动画展示。使用 `animate-interval` 标志配合此[代码](https://github.com/terrastruct/d2-docs/blob/f5c762223ce192338d9d7865df3ca8533d683cdc/static/bespoke-d2/grid-row-dominant.d2#L1)。稍后在[组合](/tour/composition/)部分会有更多介绍。
:::

## 间距大小

你可以使用以下 3 个关键字来控制网格的间距大小：
- `vertical-gap`
- `horizontal-gap`
- `grid-gap`

设置 `grid-gap` 相当于同时设置 `vertical-gap` 和 `horizontal-gap`。

`vertical-gap` 和 `horizontal-gap` 可以覆盖 `grid-gap`。

### 间距为 0

`grid-gap: 0` 尤其可以创建一些有趣的结构：

#### 比如这张日本地图

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/japan.svg2')}}></div>

> [D2 源码](https://github.com/terrastruct/d2/blob/master/docs/examples/japan-grid/japan.d2)

#### 或者一个数据表格

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/table.svg2')}}></div>

<CodeBlock className="language-d2">
    {Table}
</CodeBlock>

:::info
不过，你可能发现使用 Markdown 表格更方便，特别是当存在重复单元格时。

<CodeBlock className="language-d2">
    {MdTable}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/md-table.svg2')}}></div>
:::

### 间距为 0

## 连接（Connections）

网格本身的连接工作方式与预期相同。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-connected.svg2')}}></div>

> 源代码[在此](https://github.com/terrastruct/d2-docs/blob/eda2d8739ce21c656e7608be48cb9067df36eb53/static/d2/grid-connected.d2)。

### 网格单元格之间的连接

网格内形状之间的连接略有不同。由于网格结构施加了布局引擎无法控制的位置，布局引擎也无法进行路径规划。因此，这些连接是中心到中心的直线段，即没有寻路功能。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-connections.svg2')}}></div>

> 源代码[在此](https://github.com/terrastruct/d2/blob/master/e2etests/testdata/files/simple_grid_edges.d2)。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-nested-connections.svg2')}}></div>

> 源代码[在此](https://github.com/terrastruct/d2/blob/master/docs/examples/vector-grid/vector-grid.d2)。

## 嵌套

目前你可以将网格图嵌套在网格图中。其他类型的嵌套即将推出。

<CodeBlock className="language-d2">
    {GridNestedGrid}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-nested-grid.svg2')}}></div>

## 使用不可见元素对齐

一种常见的对齐网格元素的技术是用不可见元素填充网格。

考虑以下图表。

<CodeBlock className="language-d2">
    {GridUnaligned}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-unaligned.svg2')}}></div>

如果居中会更好看。这可以通过添加 2 个不可见元素来实现。

<CodeBlock className="language-d2">
    {GridAligned}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-aligned.svg2')}}></div>

## 故障排除

### 为什么某个单元格中有多余的内边距？

网格列中的元素宽度相同，网格行中的元素高度相同。

所以在这个例子中，"Backend Node"中存在一个小的空白区域。

<CodeBlock className="language-d2" expandeable={true}>
    {GridPadding1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-padding-1.svg2')}}></div>

这是因为 "Flask Pod" 的标签比 "Next Pod" 稍长。解决方法是设置相同的 `width`。

<CodeBlock className="language-d2" expandeable={true}>
    {GridPadding2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/grid-padding-2.svg2')}}></div>
