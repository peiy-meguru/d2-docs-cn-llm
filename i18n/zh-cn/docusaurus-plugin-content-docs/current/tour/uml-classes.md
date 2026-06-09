import CodeBlock from '@theme/CodeBlock';
import Classes1 from '@site/static/d2/classes-1.d2';
import Classes2 from '@site/static/d2/classes-2.d2';
import Classes3 from '@site/static/bespoke-d2/classes-3.d2';

# UML 类（UML Classes）

## 基础

D2 完全支持 UML 类图。以下是一个最小示例：

<CodeBlock className="language-d2">
    {Classes1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/classes-1.svg2')}}></div>

`class` 形状的每个键定义一个字段或方法。

字段键的值是其类型。

任何包含 `(` 的键都是方法，其值为返回类型。

没有值的方法键的返回类型为 void。

:::info 转义保留关键字
如果你想使用保留关键字，请用引号包裹。

```d2
my_class: {
  shape: class
  "label": string
}
```
:::

## 可见性（Visibilities）

你还可以使用 UML 风格的前缀来表示字段/方法的可见性。

| 可见性前缀 | 含义     |
| ---------- | -------- |
| 无         | public   |
| +          | public   |
| -          | private  |
| #          | protected |

参见 https://www.uml-diagrams.org/visibility.html

以下是一个具有不同可见性和更复杂类型的示例：

<CodeBlock className="language-d2">
    {Classes2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/classes-2.svg2')}}></div>

## 完整示例

<CodeBlock className="language-d2" layout="elk">
    {Classes3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/classes-3.svg2')}}></div>
