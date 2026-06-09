import CodeBlock from '@theme/CodeBlock';
import Connections1 from '@site/static/d2/connections-1.d2';
import Connections2 from '@site/static/d2/connections-2.d2';
import Connections3 from '@site/static/d2/connections-3.d2';
import Connections4 from '@site/static/d2/connections-4.d2';
import Connections5 from '@site/static/d2/connections-5.d2';
import ConnectionsReference from '@site/static/d2/connections-reference.d2';

# Connections（连接）

connection（连接）定义了 shape（形状）之间的关系。

## 基础

shape（形状）之间的连字符/箭头定义了一个 connection（连接）。

```d2
Write Replica Canada <-> Write Replica Australia

Read Replica <- Master
Write Replica -> Master

Read Replica 1 -- Read Replica 2
```

如果在一个 connection（连接）中引用了未声明的 shape（形状），该 shape（形状）会被创建（如 [hello world](hello-world.md) 示例所示）。

:::info
定义 connection（连接）有 4 种有效方式：

- `--`
- `->`
- `<-`
- `<->`

:::

### 连接标签

```d2
Read Replica 1 -- Read Replica 2: Kept in sync
```

### 连接必须引用形状的 key（键），而非其 label（标签）。

```d2
be: Backend
fe: Frontend

# 这会创建新的形状
Backend -> Frontend

# 这会通过已有标签定义连接
be -> fe
```

## 示例

<CodeBlock className="language-d2">
    {Connections1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/connections-1.svg2')}}></div>

## 重复连接

重复 connection（连接）不会覆盖已有 connection（连接），而是声明新的 connection（连接）。

<CodeBlock className="language-d2">
    {Connections2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/connections-2.svg2')}}></div>

## 连接链式书写

为了提高可读性，在一行中定义多个 connection（连接）可能看起来更自然。

<CodeBlock className="language-d2">
    {Connections3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/connections-3.svg2')}}></div>

## 循环是允许的

<CodeBlock className="language-d2">
    {Connections4}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/connections-4.svg2')}}></div>

## 箭头

要覆盖默认的 arrowhead（箭头）形状或为箭头旁添加 label（标签），可以在 connection（连接）上定义名为 `source-arrowhead` 和/或 `target-arrowhead` 的特殊 shape（形状）。

<CodeBlock className="language-d2">
    {Connections5}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/connections-5.svg2')}}></div>

:::info Arrowhead（箭头）选项
- `triangle`（三角形，默认）
  - 可通过 `style.filled: false` 进一步设置样式。
- `arrow`（箭头，比三角形更尖）
  - 可通过 `style.filled: true` 进一步设置样式。
- `diamond`（菱形）
  - 可通过 `style.filled: true` 进一步设置样式。
- `circle`（圆形）
  - 可通过 `style.filled: true` 进一步设置样式。
- `box`（方框）
  - 可通过 `style.filled: true` 进一步设置样式。
- `cf-one`、`cf-one-required`（cf 表示鸦爪式）
- `cf-many`、`cf-many-required`
- `cross`（十字）
:::

:::info
建议 arrowhead（箭头）label（标签）保持简短。它们不像常规 label（标签）那样经过自动布局优化定位，因此较长的 arrowhead（箭头）label（标签）更容易与周围对象发生碰撞。
:::

:::caution
如果 connection（连接）没有端点，arrowhead（箭头）将不起作用。

例如，以下代码将不起作用，因为没有 source-arrowhead（源箭头）。

```d2
x -> y: {
  source-arrowhead.shape: diamond
}
```
:::

## 引用连接

你可以通过指定原始 ID 后跟其 index（索引）来引用 connection（连接）。

<CodeBlock className="language-d2">
    {ConnectionsReference}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/connections-reference.svg2')}}></div>
