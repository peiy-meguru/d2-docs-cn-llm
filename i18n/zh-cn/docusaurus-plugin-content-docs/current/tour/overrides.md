import CodeBlock from '@theme/CodeBlock';
import Overrides1 from '@site/static/d2/overrides-1.d2';
import Overrides2 from '@site/static/d2/overrides-2.d2';
import NullBasic from '@site/static/d2/null-basic.d2';
import NullConnection from '@site/static/d2/null-connection.d2';
import NullAttribute from '@site/static/d2/null-attribute.d2';
import NullImplicitConnection from '@site/static/d2/null-implicit-connection.d2';
import NullImplicitDescendant from '@site/static/d2/null-implicit-descendant.d2';

# 覆写（Overrides）

如果你重新声明一个形状，新的声明会与之前的声明合并。

<CodeBlock className="language-d2">
    {Overrides1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/overrides-1.svg2')}}></div>

最新的显式标签设置具有优先级。

以下是一个涉及容器的更复杂覆写示例：

<CodeBlock className="language-d2">
    {Overrides2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/overrides-2.svg2')}}></div>

## 空值（Null）

你可以使用值 `null` 进行覆写，以删除形状、连接或属性。

<CodeBlock className="language-d2">
    {NullBasic}
</CodeBlock>

<div style={{width: 200}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/null-basic.svg2')}}></div>

这何时有用？
- [导入](/tour/imports/)同事的图表并移除不需要的内容。
- [多面板组合](/tour/composition/)中，继承面板上除某些例外之外的所有对象。
- 使用 [globs](/tour/globs/) 在一批对象之间定义连接，但排除特定对象。

### 空值化连接

<CodeBlock className="language-d2">
    {NullConnection}
</CodeBlock>

<div style={{width: 200}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/null-connection.svg2')}}></div>

### 空值化属性

<CodeBlock className="language-d2">
    {NullAttribute}
</CodeBlock>

<div style={{width: 200}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/null-attribute.svg2')}}></div>


### 隐式空值

如果将一个带有连接的形状设为 null，其连接也会被设为 null（因为 D2 中的每个连接都需要端点）。

<CodeBlock className="language-d2">
    {NullImplicitConnection}
</CodeBlock>

<div style={{width: 200}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/null-implicit-connection.svg2')}}></div>

如果将一个带有子级的形状设为 null，这些子级也会被设为 null。

<CodeBlock className="language-d2">
    {NullImplicitDescendant}
</CodeBlock>

<div style={{width: 200}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/null-implicit-descendant.svg2')}}></div>
