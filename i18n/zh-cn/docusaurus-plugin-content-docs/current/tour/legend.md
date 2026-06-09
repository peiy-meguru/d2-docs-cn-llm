import CodeBlock from '@theme/CodeBlock';
import Legend from '@site/static/d2/legend.d2';
import LegendHidden from '@site/static/d2/legend-hidden.d2';

# 图例（Legend）

使用特殊变量 `d2-legend` 来声明图例。

<CodeBlock className="language-d2">
    {Legend}
</CodeBlock>

<div style={{width: "100%"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/legend.svg2')}}></div>

## 隐藏形状

由于 `a -> b` 声明了 3 个事物（1 个连接和 2 个形状），所以图例中会显示 3 个事物。如果你只想在图例中显示连接，可以将形状的不透明度设置为排除它们。

<CodeBlock className="language-d2">
    {LegendHidden}
</CodeBlock>

<div style={{width: "100%"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/legend-hidden.svg2')}}></div>

## 重命名"图例"

只需为图例指定一个标签即可重命名。这对非英语图表尤其有用。

```d2
vars: {
  d2-legend: "凡例" {
    # 图例项...
  }
}
# 图表其余部分...
```
