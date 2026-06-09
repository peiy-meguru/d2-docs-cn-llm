import CodeBlock from '@theme/CodeBlock';
import GlobsIntro from '@site/static/d2/globs-intro.d2';
import GlobsLazy from '@site/static/d2/globs-lazy.d2';
import GlobsCasing from '@site/static/d2/globs-casing.d2';
import GlobsMultiple from '@site/static/d2/globs-multiple.d2';
import GlobsConnections from '@site/static/d2/globs-connections.d2';
import GlobsIndexedConnections from '@site/static/d2/globs-indexed-connections.d2';
import GlobsScope from '@site/static/d2/globs-scope.d2';
import GlobsRecursive from '@site/static/d2/globs-recursive.d2';
import GlobsRecursive2 from '@site/static/d2/globs-recursive-2.d2';
import GlobsFilter from '@site/static/d2/globs-filter.d2';
import GlobsFilter2 from '@site/static/d2/globs-filter-2.d2';
import GlobsFilter3 from '@site/static/d2/globs-filter-3.d2';
import GlobsFilterAnd from '@site/static/d2/globs-filter-and.d2';
import GlobsFilterEndpoints from '@site/static/d2/globs-filter-endpoints.d2';
import GlobsFilterGlobValue from '@site/static/d2/globs-filter-glob-value.d2';
import GlobsInverseFilter from '@site/static/d2/globs-inverse-filter.d2';
import GlobsNested from '@site/static/d2/globs-nested.d2';
import Defaults from '@site/static/d2/defaults.d2';

# 通配（Globs）

:::note 词源
> glob 命令是 global 的缩写，源自贝尔实验室 Unix 的最早版本……用于在未引用的参数中扩展通配符……

[https://en.wikipedia.org/wiki/Glob_(programming)](https://en.wikipedia.org/wiki/Glob_(programming))
:::

Globs（通配）是一项强大的语言特性，可以用一行代码进行全局更改。

<CodeBlock className="language-d2">
    {GlobsIntro}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-intro.svg2')}}></div>

## Globs 向后和向前应用

在以下示例中，指令如下：
1. 创建一个形状 `a`。
2. 应用一条 glob 规则。这会立即应用于现有形状，即 `a`。
3. 创建一个形状 `b`。现有的 glob 规则会重新评估，如果符合条件则应用。这里符合，因此应用于 `b`。
4. `c` 同理。

<CodeBlock className="language-d2">
    {GlobsLazy}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-lazy.svg2')}}></div>

## Globs 不区分大小写

<CodeBlock className="language-d2">
    {GlobsCasing}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-casing.svg2')}}></div>

## Globs 可以多次出现

<CodeBlock className="language-d2">
    {GlobsMultiple}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-multiple.svg2')}}></div>

## Glob 连接

你可以使用 globs 来创建连接。

<CodeBlock className="language-d2">
    {GlobsConnections}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-connections.svg2')}}></div>

:::info
注意自连接被省略了。虽然这与你对 globs 的预期不完全一致，但我们认为这种行为更实用。
:::

你也可以使用 globs 来定位修改现有连接。

<CodeBlock className="language-d2">
    {GlobsIndexedConnections}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-indexed-connections.svg2')}}></div>

## 作用域 Globs

注意在下面的示例中，globs 仅应用于它们被指定的作用域。

<CodeBlock className="language-d2">
    {GlobsScope}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-scope.svg2')}}></div>

## 递归 Globs

`**` 表示递归目标。

<CodeBlock className="language-d2">
    {GlobsRecursive}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-recursive.svg2')}}></div>

<CodeBlock className="language-d2">
    {GlobsRecursive2}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-recursive-2.svg2')}}></div>


:::info
注意 `machine B` 没有被捕获。与 `* -> *` 省略自连接的例外类似，连接中的递归 globs 也出于实用图表设计的考虑而设定了例外：它仅应用于非容器（即叶子）形状。
:::

## 过滤器

使用 `&` 来过滤 globs 的目标。你可以使用任何保留关键字进行过滤。

<CodeBlock className="language-d2">
    {GlobsFilter}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-filter.svg2')}}></div>

### 属性过滤器

除了保留关键字之外，还有特殊的属性过滤器用于更精确的目标定位。

- `connected: true|false`
- `leaf: true|false`

<CodeBlock className="language-d2">
    {GlobsFilter3}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-filter-3.svg2')}}></div>

### 数组值上的过滤器

如果被过滤的属性是数组值，则过滤器会匹配数组中的任意元素。

<CodeBlock className="language-d2">
    {GlobsFilter2}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-filter-2.svg2')}}></div>

### Globs 作为过滤器值

Globs 也可以出现在过滤器的值中。`*` 本身作为过滤器的值表示该键必须被指定。

<CodeBlock className="language-d2">
    {GlobsFilterGlobValue}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-filter-glob-value.svg2')}}></div>

### AND 过滤器

添加多行过滤器相当于 AND 操作。

<CodeBlock className="language-d2">
    {GlobsFilterAnd}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-filter-and.svg2')}}></div>

### 连接端点过滤器

连接可以根据其源形状和目标形状的属性进行过滤。

<CodeBlock className="language-d2">
    {GlobsFilterEndpoints}
</CodeBlock>

端点过滤器也支持 ID，例如 `&src: b`。

:::info
端点 ID 是绝对路径。例如，即使 glob 声明在 `a` 内部，也使用 `a.c` 而非 `c`。
:::

## 反向过滤器

使用 `!&` 来反向过滤 globs 的目标。

<CodeBlock className="language-d2">
    {GlobsInverseFilter}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-inverse-filter.svg2')}}></div>

## 嵌套 Globs

你可以嵌套 globs，结合上述功能。

<CodeBlock className="language-d2">
    {GlobsNested}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/globs-nested.svg2')}}></div>

## 全局 Globs

三重 globs 全局应用于整个图表。双 glob 和三重 glob 的区别在于，三重 glob 将应用于嵌套的 `layers`（有关 `layers` 的更多信息，请参阅[组合](/tour/composition/)章节），并且会跨导入持久化。

```d2
***.style.fill: yellow
**.shape: circle
*.style.multiple: true

x: {
  y
}

layers: {
  next: {
    a
  }
}
```

<embed src={require('@site/static/img/generated/triple-glob.pdf').default} width="100%" height="800"
 type="application/pdf" />

:::info 导入
如果导入一个文件，其中声明的 globs 通常不会被继承。三重 globs 是例外——由于它们是全局的，导入包含三重 glob 的文件也会继承该 glob。
:::

## 更改默认值

globs 的一个常见用途是更改主题的默认样式。

<CodeBlock className="language-d2">
    {Defaults}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/defaults.svg2')}}></div>
