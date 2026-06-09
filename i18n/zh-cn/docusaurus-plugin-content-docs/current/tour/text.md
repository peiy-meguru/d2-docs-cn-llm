---
sidebar_label: 文本与代码
pagination_next: tour/icons
---
import CodeBlock from '@theme/CodeBlock';
import Markdown from '@site/static/d2/markdown.d2';
import MarkdownLabel from '@site/static/d2/markdown-label.d2';
import Text2 from '@site/static/d2/text-2.d2';
import Code2 from '@site/static/d2/code-2.d2';
import NonMarkdownText from '@site/static/d2/non-markdown-text.d2';
import Latex from '@site/static/d2/latex.d2';

# 文本（Text）

## 独立文本即 Markdown

<CodeBlock className="language-d2">
    {Markdown}
</CodeBlock>

<div style={{width: 300, margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/markdown.svg2')}}></div>

## Markdown 标签（label）

如果你想在形状上设置 Markdown 标签，必须显式声明该形状。

<CodeBlock className="language-d2">
    {MarkdownLabel}
</CodeBlock>

<div style={{width: 300, margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/markdown-label.svg2')}}></div>

## 支持大多数语言

D2 很可能支持你想使用的任何语言，包括非拉丁语系的语言，如中文、日文、韩文，甚至 emoji！

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/unicode.svg2')}}></div>

## LaTeX

你可以使用 `latex` 或 `tex` 来指定一个 LaTeX 语言块。

<CodeBlock className="language-d2">
    {Text2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/text-2.svg2')}}></div>

关于 LaTeX 块的几点说明：

- LaTeX 块不响应 `font-size` 样式。你需要在 LaTeX 脚本内部使用以下命令来设置样式：
  - `\tiny{ }`
  - `\small{ }`
  - `\normal{ }`
  - `\large{ }`
  - `\huge{ }`
- 底层使用的是 [MathJax](https://www.mathjax.org/)。它不是完整的 LaTeX（完整的 LaTeX 包含文档排版引擎）。D2 的 LaTeX 块用于显示数学符号，但不支持现有 LaTeX 文档的格式。请参见[此处](https://docs.mathjax.org/en/latest/input/tex/macros/index.html)查看所有支持的命令列表。

:::caution
D2 运行在最新版的 MathJax 上，它有很多优点，但遗憾的是不支持换行。你可以通过 `displaylines` 命令来绕过这个问题。见下文。
:::

## 代码（Code）

将 `md` 改为编程语言即可得到代码块

<CodeBlock className="language-d2">
    {Code2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/code-2.svg2')}}></div>

:::info 支持的语法高亮语言
有关支持语言的完整列表，请参阅 [Chroma 库](https://github.com/alecthomas/chroma?tab=readme-ov-file#supported-languages)。

D2 还提供了方便的短别名：
- `md` → `markdown`
- `tex` → `latex`
- `js` → `javascript`
- `go` → `golang`
- `py` → `python`
- `rb` → `ruby`
- `ts` → `typescript`

如果某种语言无法识别，D2 将回退为纯文本渲染，不进行语法高亮。
:::

## 进阶：非 Markdown 文本

在某些情况下，你可能需要非 Markdown 文本。也许你只是不喜欢 Markdown，或者不喜欢 D2 所使用的 GitHub 风格的 Markdown，或者你想快速将形状改为文本。只需设置 `shape: text` 即可。

<CodeBlock className="language-d2">
    {NonMarkdownText}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/non-markdown-text.svg2')}}></div>

## 进阶：块字符串

如果你正在编写 Typescript，其中管道符号 `|` 经常被使用怎么办？只需再加一个管道符 `||`。

```d2
my_code: ||ts
  declare function getSmallPet(): Fish | Bird;
||
```

实际上，Typescript 也使用 `||`，所以这样也行不通。我们继续加。

```d2
my_code: |||ts
  declare function getSmallPet(): Fish | Bird;
  const works = (a > 1) || (b < 2)
|||
```

可能在某些语言或场景中也会使用三个管道符。D2 实际上允许你在第一个管道符之后使用任何特殊符号（非字母数字、空格或 `_`）：

```d2
# 更简洁了！
my_code: |`ts
  declare function getSmallPet(): Fish | Bird;
  const works = (a > 1) || (b < 2)
`|
```

## 进阶：LaTeX 插件

D2 包含以下 LaTeX 插件：

<CodeBlock className="language-d2">
    {Latex}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/latex.svg2')}}></div>
