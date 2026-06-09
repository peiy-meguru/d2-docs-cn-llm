import CodeBlock from '@theme/CodeBlock';
import Animated from '@site/static/bespoke-d2/animated.d2';

# 场景（Scenarios）

"场景"（Scenario）代表基础层的不同视图。

每个场景都继承自其基础层。任何新对象都会添加到基础层的所有对象之上，你可以引用基础层中的任何对象来更新它们。

注意在下面的场景中，我们只是将某些对象的不透明度降低，并定义一个新的连接来展示部署图的替代视图。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/animated.svg2')}}></div>

<CodeBlock className="language-d2-incomplete">
    {Animated}
</CodeBlock>
