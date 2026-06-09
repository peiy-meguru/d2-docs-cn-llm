import CodeBlock from '@theme/CodeBlock';
import Tables1 from '@site/static/d2/tables-1.d2';
import Tables2 from '@site/static/d2/tables-2.d2';
import Tables3 from '@site/static/d2/tables-3.d2';

# SQL 表（SQL Tables）

## 基础

你可以使用 `sql_table` 形状轻松地在 D2 中绘制实体关系图（ERD）。以下是一个最小示例：

<CodeBlock className="language-d2">
    {Tables1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/tables-1.svg2')}}></div>

SQL Table 形状的每个键定义一行。每行的主要值（冒号后面的部分）定义其类型。

每行的约束值（constraint）定义其 SQL 约束。D2 会识别并缩写：

| constraint  | 缩写 |
| ----------- | ---- |
| primary_key | PK   |
| foreign_key | FK   |
| unique      | UNQ  |

但你可以设置任何你想要的约束。如果无法识别，只是不会缩写而已。

:::info
你也可以使用数组指定多个约束。

```d2
x: int { constraint: [primary_key; unique] }
```
:::

:::info 转义保留关键字
如果你想使用保留关键字，请用引号包裹。

```d2
my_table: {
  shape: sql_table
  "label": string
}
```
:::

## 外键（Foreign Keys）

以下是如何定义两个表之间的外键连接的示例：

<CodeBlock className="language-d2">
    {Tables2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/tables-2.svg2')}}></div>

:::info
使用 [TALA 布局引擎](/tour/tala/)或 [ELK 布局引擎](/tour/elk/)渲染时，连接会精确指向对应的行。
:::

## 示例

与所有其他形状一样，你可以将 `sql_table` 嵌套到容器中，并定义从其他形状到它们的边。以下是一个示例：

<CodeBlock className="language-d2">
    {Tables3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/tables-3.svg2')}}></div>
