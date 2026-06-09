---
sidebar_label: D2 是什么
pagination_next: tour/experience
---
import CodeBlock from '@theme/CodeBlock';
import Example from '@site/static/bespoke-d2/terminal-theme.d2';

# D2 导览

**D2** 是一种图表脚本语言，可以将文本转换为图表。它代表 **Declarative Diagramming（声明式图表）**。所谓声明式，即你只需描述想要图表化的内容，它会自动生成图像。

例如，下载 CLI，创建一个名为 `input.d2` 的文件，复制粘贴以下内容，运行此命令，即可得到下图。

```sh
d2 --theme=300 --dark-theme=200 -l elk --pad 0 ./input.d2
```

<div style={{width: "100%"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/terminal-theme.svg2')}}></div>

<CodeBlock className="language-d2">
    {Example}
</CodeBlock>

## 使用 CLI 监视模式

<img className="screenCap" width="100%" src={require('@site/static/img/screenshots/cli.gif').default}
alt="D2 CLI"/>

你可以在大约 5-10 分钟内完成本导览，最后会有一份速查表供你下载参考。如果你只想要最基本的内容，<a
href="/tour/hello-world/">开始使用</a>大约需要
2 分钟。

:::info
D2 的源代码托管在此：
[https://github.com/terrastruct/d2](https://github.com/terrastruct/d2)。

本文档的源代码在此：
[https://github.com/terrastruct/d2-docs](https://github.com/terrastruct/d2-docs)。
:::

:::info
对于每个 D2 代码片段，你可以悬停并在 Playground 中直接打开和调试。

有些例外，例如使用导入（import）功能的代码片段。
:::
