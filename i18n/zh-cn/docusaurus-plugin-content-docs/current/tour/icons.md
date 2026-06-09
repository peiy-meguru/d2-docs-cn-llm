---
sidebar_label: 图标与图片
---
import CodeBlock from '@theme/CodeBlock';
import Icons1 from '@site/static/d2/icons-1.d2';
import IconPlacement from '@site/static/d2/icon-placement.d2';
import IconsImage from '@site/static/d2/icons-image.d2';

# 图标（Icons）

:::tip
我们免费托管了一套软件架构图中常见的图标集合，帮助你快速上手：[https://icons.terrastruct.com](https://icons.terrastruct.com)。
:::

图标和图片是制作生产级图表的重要组成部分。

你可以使用任何 URL 作为值。

<CodeBlock className="language-d2">
    {Icons1}
</CodeBlock>

<div style={{width: "200px", margin: "0 auto 20px auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/icons-1.svg2')}}></div>

:::info
在本地使用 D2 CLI？你可以指定本地图片，如 `icon: ./my_cat.png`。
:::

图标位置是自动的。具体考虑因素因布局引擎而异，但诸如是否与标签共存、是否为容器等因素通常会影响图标的放置位置，以避免遮挡。请注意，下图中容器图标位于左上角，而非容器图标位于中心。

<CodeBlock className="language-d2">
    {IconPlacement}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/icon-placement.svg2')}}></div>

:::info
图标可以使用 `near` 关键字进行定位，详见[后续章节](/tour/positions/#label-and-icon-positioning)。
:::

## 添加 `shape: image` 以创建独立图标形状

<CodeBlock className="language-d2">
    {IconsImage}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/icons-image.svg2')}}></div>
