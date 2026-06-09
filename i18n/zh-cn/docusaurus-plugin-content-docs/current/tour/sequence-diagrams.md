import CodeBlock from '@theme/CodeBlock';
import WebPImage from '@site/src/components/WebPImage';
import SequenceDiagrams1 from '@site/static/d2/sequence-diagrams-1.d2';
import SequenceDiagrams2 from '@site/static/d2/sequence-diagrams-2.d2';
import SequenceDiagrams3 from '@site/static/d2/sequence-diagrams-3.d2';
import SequenceDiagrams4 from '@site/static/d2/sequence-diagrams-4.d2';
import SequenceDiagramsScope from '@site/static/d2/sequence-diagrams-scope.d2';
import SequenceDiagramsGroup from '@site/static/d2/sequence-diagrams-group.d2';
import SequenceDiagramsNote from '@site/static/d2/sequence-diagrams-note.d2';
import SequenceDiagramsSelf from '@site/static/d2/sequence-diagrams-self.d2';
import SequenceDiagramsLifeline from '@site/static/d2/sequence-diagrams-lifeline.d2';

# 序列图（Sequence Diagrams）

序列图通过在对象上设置 `shape: sequence_diagram` 来创建。

<CodeBlock className="language-d2">
    {SequenceDiagrams1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-1.svg2')}}></div>

## 规则

与其他工具不同，序列图无需学习特殊语法。规则也几乎与 D2 中其他任何地方完全相同，但有两点显著差异。

### 作用域（Scoping）

序列图的子元素在整个序列图中共享相同的作用域。

例如：

<CodeBlock className="language-d2">
    {SequenceDiagramsScope}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-scope.svg2')}}></div>

在序列图之外，`alice` 和 `bob` 会有多个实例，因为它们具有不同的容器作用域。但在 `shape: sequence_diagram` 下嵌套时，它们指向的是同一个 `alice` 和 `bob`。

### 排序（Ordering）

在 D2 的其他地方，没有排序的概念。如果你在一个连接之后定义另一个连接，并不能保证它在视觉上会出现在后面。然而，在序列图中，顺序很重要。你定义所有内容的顺序就是它们出现的顺序。

这包括角色（actors）。你不必显式定义角色（除非它们首次出现在组中），但如果你想要定义特定的顺序，你应该这样做。

```d2
shape: sequence_diagram
# 记住分号允许在一行中定义多个对象
# 角色将按从左到右的顺序显示为 a、b、c、d...
a; b; c; d
# ... 即使连接的顺序不同
c -> d
d -> a
b -> d
```

:::info
D2 中的角色（actor）在其他工具中也称为"参与者"（participant）。
:::

## 功能特性

### 序列图是 D2 对象

与 D2 中的其他所有对象一样，它们可以被包含、连接、重新标记、重新设置样式，并像其他任何对象一样处理。

<CodeBlock className="language-d2">
    {SequenceDiagrams2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-2.svg2')}}></div>

### 跨度（Spans）

跨度表示序列图中交互的开始和结束。

:::info
D2 中的跨度（span）在其他工具中也称为"生命周期"（lifespan）、"激活框"（activation box）和"激活条"（activation bar）。
:::

你可以通过在角色上连接一个嵌套对象来指定跨度。

<CodeBlock className="language-d2">
    {SequenceDiagrams3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-3.svg2')}}></div>

### 分组（Groups）

分组帮助你标记序列图的一个子集。

:::info
D2 中的分组（group）在其他工具中也称为"片段"（fragment）、"边界组"（edge group）和"框架"（frame）。
:::

我们在之前的解释作用域规则的例子中已经见过一个例子。更正式地说，分组是 `sequence_diagram` 形状内的一个容器，它不与任何内容连接，但内部包含连接或对象。

<CodeBlock className="language-d2">
    {SequenceDiagramsGroup}
</CodeBlock>

:::caution
由于序列图中独特的作用域规则，当你在分组内时，连接中引用的对象必须存在于顶层。请注意，在上面的示例中，`alice` 和 `bob` 在分组声明之前被显式声明。
:::

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-group.svg2')}}></div>

### 注释（Notes）

注释通过在一个角色上定义一个没有连接指向它的嵌套对象来声明。

<CodeBlock className="language-d2">
    {SequenceDiagramsNote}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-note.svg2')}}></div>

### 自消息（Self-messages）

自引用消息可以声明为从一个角色指向自身。

<CodeBlock className="language-d2">
    {SequenceDiagramsSelf}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-self.svg2')}}></div>

### 自定义

你可以像其他任何形状一样设置形状和连接的样式。这里我们将一些消息设为虚线，并在角色上设置形状。

<CodeBlock className="language-d2">
    {SequenceDiagrams4}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-4.svg2')}}></div>

生命线边（那些从上到下的线条）继承角色的 `stroke` 和 `stroke-dash` 样式。

<CodeBlock className="language-d2">
    {SequenceDiagramsLifeline}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/sequence-diagrams-lifeline.svg2')}}></div>

## 术语表（Glossary）

<WebPImage src={require('@site/static/img/screenshots/sequence_glossary.png').default} webpSrc={require('@site/static/img/screenshots/sequence_glossary.webp').default}
alt="sequence diagram glossary"/>
