---
pagination_next: tour/shapes
---
import CodeBlock from '@theme/CodeBlock';
import HelloWorld from '@site/static/d2/hello-world.d2';

# Hello World

<CodeBlock className="language-d2">
    {HelloWorld}
</CodeBlock>

<div
className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/hello-world.svg2')}}></div>

这里声明了两个 shape（形状）`x` 和 `y` 之间的 connection（连接），并带有 label（标签）`hello world`。
