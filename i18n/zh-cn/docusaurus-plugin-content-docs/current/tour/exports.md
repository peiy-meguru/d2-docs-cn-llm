# 导出（Exports）

import WebPImage from '@site/src/components/WebPImage';

在 CLI 上，你可以将 `.d2` 导出为：
* [SVG](#svg)
* [PNG](#png)
* [PDF](#pdf)
* [PPTX](#pptx)
* [GIF](#gif)
* [ASCII](#ascii)
* [Stdout](#stdout)

## SVG

```shell
d2 in.d2 out.svg
```

SVG 是 CLI 上的默认导出格式。如果你不指定输出，导出文件将以输入名称作为 SVG 文件名。

例如，`d2 in.d2` 将生成一个名为 `in.svg` 的文件。

生成的 SVG 中注入了 CSS。这加上使用 HTML `<foreignObject>` 来支持 Markdown，意味着 SVG 旨在 Web 环境中查看。例如，在浏览器中打开它，或嵌入到网页中。在没有 Web 环境的情况下（如在 Inkscape 或 Adobe Illustrator 中），可能无法正确显示。

在 CLI 上，如果你传递 `-`
- 作为输入，则从 stdin 读取 D2
- 作为输出，则将 SVG 写入 stdout

:::info SVG 导出的技术细节 如果你计划对 SVG 导出进行后处理，这些信息可能有用。

**元素 ID**：所有形状元素都会获得带有 base64 编码 ID 的 CSS 类，以确保安全的 CSS 定位。例如，ID 为 `my-shape` 的形状会获得类 `bXktc2hhcGU`（"my-shape" 的 base64 编码）。

**唯一标识符**：每个图表都会获得一个确定性哈希前缀（例如 `d2-1234567890`），用于剪切路径、渐变和其他 SVG 元素，以防止同一页面上多个图表发生冲突。
:::

## PNG

```shell
d2 in.d2 out.png
```

PNG 导出通过 [Playwright](https://github.com/microsoft/playwright) 启动无头浏览器，将 SVG 放入其中并截图。Playwright 的首次调用将下载其依赖项（如果机器上尚不存在）。

:::info
如果你收到类似 `err: failed to launch Chromium` 的消息，可以尝试在机器上独立于 D2 安装 Playwright 依赖项。例如：

```
npm install -g @playwright
npx playwright install --with-deps chromium
```

更多信息请参见 [#744](https://github.com/terrastruct/d2/issues/744#issuecomment-1446641870)。
:::

## PDF

```shell
d2 in.d2 out.pdf
```

PDF 导出是将 PNG 导出放置到 PDF 页面上，并添加页眉和字体的结果。因此，PNG 导出所需的依赖项也是 PDF 导出所需的。

PDF 比 PNG 更具交互性，但比 SVG 交互性弱。

例如，`animate` 关键字不会像在 SVG 中那样在 PDF 导出中显示。

但 `link` 在 PDF 中仍然可以点击。

<WebPImage src={require('@site/static/img/screenshots/linked_pdf.png').default} webpSrc={require('@site/static/img/screenshots/linked_pdf.webp').default} alt="D2 中带链接的 PDF 示例" width={500}/>

## PPTX

```shell
d2 in.d2 out.pptx
```

类似于 PDF 导出。此导出格式与组合（例如具有多个图层、场景、步骤的图表）配合使用时，非常适合进行演示。

## GIF

```shell
d2 in.d2 out.gif
```

此导出格式与短组合配合使用时，非常适合进行演示。例如，显示两个场景，展示几个步骤。观众可以在几秒钟的循环中消化内容，无需手动翻阅。

## ASCII

:::warning 测试版
ASCII 输出是 0.7.1 版本的新功能。它们被视为测试版，许多图表可能无法正确渲染。
:::

ASCII 导出将图表渲染为基于文本的艺术，非常适合文档、终端和不适合图形格式的环境。D2 会自动检测 `.txt` 文件扩展名并以 ASCII 格式渲染。

```shell
d2 in.d2 out.txt
```

### 字符集

D2 支持两种 ASCII 字符模式：

#### 扩展模式（默认）
使用 Unicode 制表符绘制字符以获得更清晰的输出：

```shell
d2 in.d2 out.txt
```

```
┌───────┐       ┌───────┐
│ Hello │──────▶│ World │
└───────┘       └───────┘
```

#### 标准模式
使用基本 ASCII 字符以获得最大兼容性：

```shell
d2 --ascii-mode standard in.d2 out.txt
```

```
+-------+       +-------+
| Hello |------>| World |
+-------+       +-------+
```

### 注意事项

- 仅使用 ELK 和 TALA 渲染，因为曲线在 ASCII 中渲染效果不佳。如果选择 Dagre（或未指定），则会使用 ELK 渲染。
- 某些形状受支持，如 Person，但某些形状难以在 ASCII 中清晰表示。如果输出是 ASCII，最好避免使用这些形状，但如果无法避免，在这些情况下，左上角的图标表示该形状的意图。
- 许多样式在 ASCII 中无效，例如阴影、多个或动画。最好保持简单的框和箭头类型图表。

## Stdout

D2 接受 `-` 代替输入和/或输出参数。SVG 用作 Stdout 输出的格式。

例如，这将编写一个包含 `x -> y` 的 D2 脚本并将其输出到文件 `example.svg`。

```shell
echo "x -> y" | d2 - - > example.svg
```
