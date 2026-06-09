import CodeBlock from '@theme/CodeBlock';
import WebPImage from '@site/src/components/WebPImage';
import NearConstant from '@site/static/d2/near-constant.d2';
import NearContainer from '@site/static/d2/near-container.d2';
import NearExplanation from '@site/static/d2/near-explanation.d2';
import NearLabelIcon from '@site/static/d2/near-label-icon.d2';
import BorderLabel from '@site/static/d2/border-label.d2';
import TooltipNear from '@site/static/d2/tooltip-near.d2';

# 位置（Positions）

通常，定位完全由布局引擎控制。这是文本转图表的主要优势之一——你不需要手动定义所有对象的位置。

然而，有时你确实希望对位置进行一些控制。目前有两种方法可以实现。

## 附近（Near）

D2 允许你将元素定位在图表周围的固定点上。

:::info 可选值
`top-left`、`top-center`、`top-right`、

`center-left`、`center-right`、

`bottom-left`、`bottom-center`、`bottom-right`
:::

让我们探讨一些用例：

### 为图表添加标题

<CodeBlock className="language-d2">
    {NearConstant}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/near-constant.svg2')}}></div>

### 创建图例

<CodeBlock className="language-d2">
    {NearContainer}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/near-container.svg2')}}></div>

### 长篇描述或说明

<CodeBlock className="language-d2">
    {NearExplanation}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/near-explanation.svg2')}}></div>

## 标签和图标定位

`near` 可以嵌套到 `label` 和 `icon` 以指定它们的位置。

<CodeBlock className="language-d2">
    {NearLabelIcon}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/near-label-icon.svg2')}}></div>

### 外部和边框

在定位标签和图标时，除了 `near` 在其他地方可以接受的值之外，还可以使用 `outside-` 前缀来指定位于形状边界框外部的定位。

`outside-top-left`、`outside-top-center`、`outside-top-right`、

`outside-left-center`、`outside-right-center`、

`outside-bottom-left`、`outside-bottom-center`、`outside-bottom-right`

注意 `outside-left-center` 是不同于 `center-left` 的顺序。

你也可以添加 `border-` 前缀来指定标签位于边框上。

<CodeBlock className="language-d2">
    {BorderLabel}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/border-label.svg2')}}></div>

## 工具提示附近（Tooltip near）

通常，`tooltip` 是悬停时显示的效果。但是，如果你指定了 `near` 字段，它将永久显示。

<CodeBlock className="language-d2">
    {TooltipNear}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/tooltip-near.svg2')}}></div>

## 指向对象的附近（Near objects）

:::info
仅适用于 TALA。我们正在努力使其在其他布局引擎中也能实现。
:::

你也可以将 `near` 设置为另一个形状的绝对 ID，以向布局引擎提示它们应该彼此靠近。

```d2
vars: {
  d2-config: {
    layout-engine: tala
  }
}
aws: {
  load_balancer -> api
  api -> db
}
gcloud: {
  auth -> db
}

gcloud -> aws

explanation: |md
  # Why do we use AWS?
  - It has more uptime than GCloud
  - We have free credits
| {
  near: aws
}
```

注意文本被定位在 `aws` 节点附近，而不是 `gcloud` 节点附近。

<WebPImage src={require('@site/static/img/screenshots/text-2.png').default} webpSrc={require('@site/static/img/screenshots/text-2.webp').default} alt="text near example" width={800}/>

## 顶部和左侧（Top and left）

在 TALA 引擎上，你也可以直接设置对象的 `top` 和 `left` 值，布局引擎只会移动其周围的其他对象。

更多信息，请参见 [TALA 用户手册](https://github.com/terrastruct/TALA/blob/master/TALA_User_Manual.pdf)第 17 页。
