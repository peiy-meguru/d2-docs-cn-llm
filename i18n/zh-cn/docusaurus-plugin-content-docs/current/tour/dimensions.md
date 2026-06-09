import CodeBlock from '@theme/CodeBlock';
import Dimensions from '@site/static/d2/dimensions.d2';

# 尺寸（Dimensions）

你可以指定大多数形状的 `width` 和 `height`。

:::info
这些关键字不能在容器上设置，因为容器会调整大小以适应其子元素。
:::

<CodeBlock className="language-d2">
    {Dimensions}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/dimensions.svg2')}}></div>
