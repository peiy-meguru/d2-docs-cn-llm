import CodeBlock from '@theme/CodeBlock';
import Shapes1 from '@site/static/d2/shapes-1.d2';
import Shapes2 from '@site/static/d2/shapes-2.d2';

# Shapes（形状）

## 基础

你可以像这样声明 shape（形状）：

<CodeBlock className="language-d2">
    {Shapes1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/shapes-1.svg2')}}></div>

你也可以使用分号在同一行定义多个 shape（形状）：

```d2
SQLite; Cassandra
```

默认情况下，shape（形状）的 label（标签）与其 key（键）相同。但如果你希望不同，可以像这样指定一个新 label（标签）：

```d2
pg: PostgreSQL
```

默认情况下，shape（形状）的类型为 `rectangle`（矩形）。要指定其他类型，提供 `shape`（形状）字段：

```d2
Cloud: my cloud
Cloud.shape: cloud
```

## 示例

<CodeBlock className="language-d2">
    {Shapes2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/shapes-2.svg2')}}></div>

:::info
key（键）不区分大小写，因此 `postgresql` 和 `postgreSQL` 将引用同一个 shape（形状）。
:::

:::info Shape（形状）目录

<div className="embedSVG overflow" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/shapes-3.svg2')}}></div>

`shape`（形状）还有其他可选值，但它们属于特殊类型，将在下一节中介绍。
:::

## 1:1 比例形状

某些 shape（形状）保持 1:1 的宽高比，即宽度和高度始终相等。

- `circle`（圆形）
- `square`（正方形）

对于这些 shape（形状），如果 label（标签）较长导致 shape（形状）变宽，D2 也会增加 shape（形状）的高度以维持 1:1 比例。

如果手动设置 1:1 比例 shape（形状）的 `width` 和 `height`，则两个维度都将设置为两个值中较大的那个，以保持宽高比。
