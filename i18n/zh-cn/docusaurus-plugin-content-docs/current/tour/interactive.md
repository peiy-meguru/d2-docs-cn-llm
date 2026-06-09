import CodeBlock from '@theme/CodeBlock';
import WebPImage from '@site/src/components/WebPImage';
import Tooltip from '@site/static/d2/tooltip.d2';
import Links from '@site/static/d2/links.d2';

# 交互（Interactive）

## 工具提示（Tooltips）

工具提示是悬停时显示的文本。它们有两个用途：
1. 添加上下文。
    - 你想为对象添加描述。它并不是每个人都需要的，但想要额外信息的人可以获取到。
2. 保持整洁。
    - 你的图表变得混乱了。与其添加更多文本，不如将一些内容藏到工具提示中。

<CodeBlock className="language-d2">
    {Tooltip}
</CodeBlock>

试试看，将鼠标悬停在 `x` 和 `y` 上。注意它们有一个图标指示它们包含工具提示。

<div
className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/tooltip.svg2')}}></div>

当你导出为 PNG 等静态格式时，D2 会
1. 将所有图标改为数字编号。
2. 添加一个附录，每一行对应一个数字。

<WebPImage style={{textAlign: 'center'}} width={500} src={require('@site/static/img/screenshots/tooltip.png').default} webpSrc={require('@site/static/img/screenshots/tooltip.webp').default} alt="d2 tooltip" />

:::caution
工具提示使用 HTML [title](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/title) 标签实现，其对文本格式的支持有限。Markdown 在工具提示中无法按预期渲染。
:::

## 链接（Links）

链接类似于工具提示，但你可以点击跳转到外部链接。

:::info
当链接包含 `#` 字符作为 URI 片段的一部分时，例如 `https://example.com/page#fragment`，请注意如果不加引号且不转义，该片段将被视为注释。
:::

<CodeBlock className="language-d2">
    {Links}
</CodeBlock>

试试点击每个链接。

<div
className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/links.svg2')}}></div>
