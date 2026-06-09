import CodeBlock from '@theme/CodeBlock';
import VarsIntro from '@site/static/d2/vars-intro.d2';
import VarsNested from '@site/static/d2/vars-nested.d2';
import VarsScoped from '@site/static/d2/vars-scoped.d2';
import VarsEscaped from '@site/static/d2/vars-escaped.d2';
import VarsSpread from '@site/static/d2/vars-spread.d2';
import VarsConfig from '@site/static/d2/vars-config.d2';

# 变量与替换（Variables & Substitutions）

`vars` 是一个特殊关键字，用于定义变量。这些变量可以通过替换语法 `${}` 来引用。

<CodeBlock className="language-d2">
    {VarsIntro}
</CodeBlock>

<div style={{width: 400}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/vars-intro.svg2')}}></div>

## 变量可以嵌套

使用 `.` 来引用嵌套变量。

<CodeBlock className="language-d2">
    {VarsNested}
</CodeBlock>

<div style={{width: 200}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/vars-nested.svg2')}}></div>

## 变量具有作用域

它们的工作原理与编程中的变量作用域类似。替换可以引用在更外层作用域中定义的变量，但不能引用更内层作用域中的变量。如果一个变量出现在两个作用域中，则使用更接近替换的那个。

<CodeBlock className="language-d2">
    {VarsScoped}
</CodeBlock>

<div style={{width: 600}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/vars-scoped.svg2')}}></div>

## 单引号绕过替换

<CodeBlock className="language-d2">
    {VarsEscaped}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/vars-escaped.svg2')}}></div>

## 展开替换

如果 `x` 是一个映射（map）或数组（array），`...${x}` 会将 `x` 的内容展开到映射或数组中。

<CodeBlock className="language-d2">
    {VarsSpread}
</CodeBlock>

<div style={{width: 400}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/vars-spread.svg2')}}></div>

## 配置变量

某些配置可以直接在 `vars` 中设置，而无需使用标志或环境变量。

<CodeBlock className="language-d2">
    {VarsConfig}
</CodeBlock>

这等同于在无 `vars` 的情况下调用以下命令：
```shell
d2 --layout=elk --theme=4 --dark-theme=200 --pad=0 --sketch --center input.d2
```

<div style={{width: 400}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/vars-config.svg2')}}></div>

:::info 优先级
标志和环境变量具有更高优先级。

换句话说，如果你调用 `D2_PAD=2 d2 --theme=1 input.d2`，那么无论 `input.d2` 的 `d2-config` 中 `theme-id` 和 `pad` 设置为何值，都将使用命令行中的选项。
:::

:::info `data`
`data` 是一个允许任意内容的键值对映射。用于第三方软件读取配置的情况，例如当 D2 作为库使用或与外部插件一起运行时。

例如，

```d2
vars: {
  d2-config: {
    data: {
      power-level: 9000
    }
  }
}
```
:::
