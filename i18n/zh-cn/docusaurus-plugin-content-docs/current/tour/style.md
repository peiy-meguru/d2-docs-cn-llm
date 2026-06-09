import CodeBlock from '@theme/CodeBlock';
import StylesOpacity from '@site/static/d2/styles-opacity.d2';
import StylesStroke from '@site/static/d2/styles-stroke.d2';
import StylesFill from '@site/static/d2/styles-fill.d2';
import StylesFillTransparent from '@site/static/d2/styles-fill-transparent.d2';
import StylesFillPattern from '@site/static/d2/styles-fill-pattern.d2';
import StylesStrokeWidth from '@site/static/d2/styles-stroke-width.d2';
import StylesStrokeDash from '@site/static/d2/styles-stroke-dash.d2';
import StylesBorderRadius from '@site/static/d2/styles-border-radius.d2';
import Pill from '@site/static/d2/pill.d2';
import StylesShadow from '@site/static/d2/styles-shadow.d2';
import Styles3d from '@site/static/d2/styles-3d.d2';
import StylesMultiple from '@site/static/d2/styles-multiple.d2';
import StylesDoubleBorder from '@site/static/d2/styles-double-border.d2';
import StylesFont from '@site/static/d2/styles-font.d2';
import StylesFontSize from '@site/static/d2/styles-font-size.d2';
import StylesFontColor from '@site/static/d2/styles-font-color.d2';
import StylesTableColor from '@site/static/d2/styles-table-color.d2';
import StylesAnimated from '@site/static/bespoke-d2/styles-animated.d2';
import StylesTextDecoration from '@site/static/d2/styles-text-decoration.d2';
import StylesTextTransform from '@site/static/d2/styles-text-transform.d2';
import StylesRoot from '@site/static/d2/styles-root.d2';

# 样式（Styles）

如果你想自定义形状的样式，可以在 `style` 字段下设置以下保留关键字。

以下是所有有效样式的目录，分别应用于此基准图。

<div style={{width: "400px", margin: "20px auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-base.svg2')}}></div>

:::note
以下 SVG 使用 `direction: right` 渲染，但为了简洁，已从显示的脚本中省略。
:::

:::tip
想要更改形状和/或连接的默认样式？请参阅[使用通配符更改默认值](/tour/globs/#changing-defaults)。
:::

## 样式关键字

- [opacity（不透明度）](#opacity)
- [stroke（描边）](#stroke)
- [fill（填充）](#fill)（仅形状）
- [fill-pattern（填充图案）](#fill-pattern)（仅形状）
- [stroke-width（描边宽度）](#stroke-width)
- [stroke-dash（描边虚线）](#stroke-dash)
- [border-radius（边框圆角）](#border-radius)
- [shadow（阴影）](#shadow)（仅形状）
- [3D（三维）](#3d)（仅矩形/正方形）
- [multiple（多重）](#multiple)（仅形状）
- [double-border（双边框）](#double-border)（矩形和椭圆形）
- [font（字体）](#font)
- [font-size（字号）](#font-size)
- [font-color（字体颜色）](#font-color)
- [animated（动画）](#animated)
- [bold, italic, underline（粗体、斜体、下划线）](#bold-italic-underline)
- [text-transform（文本转换）](#text-transform)
- [root（根）](#root)

## 不透明度（Opacity）

介于 `0` 和 `1` 之间的浮点数。

<CodeBlock className="language-d2">
    {StylesOpacity}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-opacity.svg2')}}></div>

## 描边（Stroke）

CSS 颜色名称、十六进制代码或 CSS 渐变字符串的子集。

<CodeBlock className="language-d2">
    {StylesStroke}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-stroke.svg2')}}></div>

<br/>

对于 `sql_table` 和 `class`，`stroke` 作为 `fill` 应用于主体（因为 `fill` 已用于控制标题的 `fill`）。

<div style={{width: "600px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-table-stroke.svg2')}}></div>

## 填充（Fill）

CSS 颜色名称、十六进制代码或 CSS 渐变字符串的子集。

<CodeBlock className="language-d2">
    {StylesFill}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-fill.svg2')}}></div>

<br/>

对于 `sql_table` 和 `class`，`fill` 应用于标题。

<div style={{width: "600px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-table-fill.svg2')}}></div>

想要透明效果？

<CodeBlock className="language-d2">
    {StylesFillTransparent}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-fill-transparent.svg2')}}></div>

## 填充图案（Fill Pattern）

可用的图案：

- `dots`
- `lines`
- `grain`
- `none`（用于取消某些主题设置的图案）

<CodeBlock className="language-d2">
    {StylesFillPattern}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-fill-pattern.svg2')}}></div>

## 描边宽度（Stroke Width）

介于 `1` 和 `15` 之间的整数。

<CodeBlock className="language-d2">
    {StylesStrokeWidth}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-stroke-width.svg2')}}></div>

## 描边虚线（Stroke Dash）

介于 `0` 和 `10` 之间的整数。

<CodeBlock className="language-d2">
    {StylesStrokeDash}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-stroke-dash.svg2')}}></div>

## 边框圆角（Border Radius）

介于 `0` 和 `20` 之间的整数。

<CodeBlock className="language-d2">
    {StylesBorderRadius}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-border-radius.svg2')}}></div>

:::info
`border-radius` 也适用于连接，控制拐角的圆角程度。这仅适用于使用拐角的布局引擎（例如 ELK），并且当然只对路径有拐角的连接有效。
:::

指定一个非常大的值会产生"胶囊"（pill）效果。

<CodeBlock className="language-d2">
    {Pill}
</CodeBlock>

<div style={{width: "200px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/pill.svg2')}}></div>

## 阴影（Shadow）

`true` 或 `false`。

<CodeBlock className="language-d2">
    {StylesShadow}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-shadow.svg2')}}></div>

## 3D（三维）

`true` 或 `false`。

<CodeBlock className="language-d2">
    {Styles3d}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-3d.svg2')}}></div>

## 多重（Multiple）

`true` 或 `false`。

<CodeBlock className="language-d2">
    {StylesMultiple}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-multiple.svg2')}}></div>

## 双边框（Double Border）

`true` 或 `false`。

<CodeBlock className="language-d2">
    {StylesDoubleBorder}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-double-border.svg2')}}></div>

## 字体（Font）

目前唯一可用的选项是 `mono`。更多选项即将推出。

<CodeBlock className="language-d2">
    {StylesFont}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-font.svg2')}}></div>

## 字号（Font Size）

介于 `8` 和 `100` 之间的整数。

<CodeBlock className="language-d2">
    {StylesFontSize}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-font-size.svg2')}}></div>

## 字体颜色（Font Color）

CSS 颜色名称、十六进制代码或 CSS 渐变字符串的子集。

<CodeBlock className="language-d2">
    {StylesFontColor}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-font-color.svg2')}}></div>

<br/>

对于 `sql_table` 和 `class`，`font-color` 仅应用于标题文本（主题控制主体中的其他颜色）。

<div style={{width: "600px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-table-color.svg2')}}></div>

## 动画（Animated）

`true` 或 `false`。

<CodeBlock className="language-d2">
    {StylesAnimated}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-animated.svg2')}}></div>

## 粗体、斜体、下划线（Bold, italic, underline）

`true` 或 `false`。

<CodeBlock className="language-d2">
    {StylesTextDecoration}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-text-decoration.svg2')}}></div>

## 文本转换（Text transform）

`text-transform` 更改标签的大小写。

- `uppercase`
- `lowercase`
- `title`
- `none`（用于取消特殊主题可能应用的大写）

<CodeBlock className="language-d2">
    {StylesTextTransform}
</CodeBlock>

<div style={{width: "400px", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-text-transform.svg2')}}></div>

## 根（Root）

某些样式可以在根级别应用。例如，要设置图表背景颜色，使用 `style.fill`。

目前支持的关键字集包括：

- `fill`：图表背景颜色
- `fill-pattern`：背景填充图案
- `stroke`：图表周围的边框
- `stroke-width`
- `stroke-dash`
- `double-border`：双边框，一种流行的边框效果

<CodeBlock className="language-d2">
    {StylesRoot}
</CodeBlock>

<div style={{width: "400px", margin: "20px auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/styles-root.svg2')}}></div>

:::info
本文档中的所有图表均使用 `pad=0` 渲染。如果你使用 `stroke` 为图表创建边框，你可能需要添加一些内边距。
:::
