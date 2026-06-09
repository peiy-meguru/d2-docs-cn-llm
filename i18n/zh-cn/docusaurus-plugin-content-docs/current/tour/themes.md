---
pagination_next: tour/style
---
import CodeBlock from '@theme/CodeBlock';
import WebPImage from '@site/src/components/WebPImage';
import TerminalTheme from '@site/static/bespoke-d2/terminal-theme.d2';

# 主题（Themes）

D2 内置了许多主题，让你的图表看起来专业且可以直接插入博客和 Wiki。

<WebPImage width={700} src={require('@site/static/img/screenshots/themes/theme_overview.png').default} webpSrc={require('@site/static/img/screenshots/themes/theme_overview.webp').default} alt="D2 theme choices"/>
<WebPImage width={400} src={require('@site/static/img/screenshots/themes/theme_2.png').default} webpSrc={require('@site/static/img/screenshots/themes/theme_2.webp').default} alt="mixed berry blue theme"/>
<WebPImage width={400} src={require('@site/static/img/screenshots/themes/theme_3.png').default} webpSrc={require('@site/static/img/screenshots/themes/theme_3.webp').default} alt="vanilla nitro cola theme"/>

### 主题同样适用于特殊形状，如表格

# 使用"Grape soda"主题渲染

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/theme-table.svg2')}}></div>

# 使用"Vanilla nitro cola"主题渲染

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/theme-table-2.svg2')}}></div>

## 在 CLI 上设置主题

要指定使用的主题，可以设置 `-t, --theme` 标志。

```shell
d2 -t 101 input.d2
```

你也可以使用环境变量。

```shell
D2_THEME=101 d2 input.d2
```

要查看可用的主题，运行

```shell
d2 themes
```

## 暗色主题（Dark theme）

暗色主题默认不会设置，因此无论用户的系统偏好是浅色还是深色，你的图表看起来都一样。

:::info
本文档中的所有图表都采用暗色主题。尝试切换你的系统偏好（浅色/深色），看看它如何变化。
:::

如果你希望图表在用户系统偏好为深色时自动切换到暗色主题，可以通过指定以下标志来实现。

```shell
d2 --dark-theme 200 input.d2
```

与常规主题一样，这也可以通过环境变量设置。

```shell
D2_DARK_THEME=200 d2 input.d2
```

:::info
主题分别归类为浅色和深色，但你也可以将暗色主题 ID 传递给 `theme`，使图表始终为深色（反之亦然，给深色模式用户一个惊喜）。
:::

暗色主题示例（这是一张图片而非 SVG，因此不会根据你的系统偏好而变化）。
<WebPImage width={600} src={require('@site/static/img/screenshots/themes/dark.png').default} webpSrc={require('@site/static/img/screenshots/themes/dark.webp').default} alt="dark theme"/>

## 特殊主题

某些特殊主题不仅仅改变颜色。

例如，当你应用 `Terminal` 主题时，会设置以下默认属性：
- 所有标签大写
- 无边框圆角
- 等宽字体
- 所有容器设置 `fill-pattern` 为 `dots`
- 最外层容器设置 `double-border` 为 `true`

<div style={{width: "100%", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/terminal-theme.svg2')}}></div>

上述图表的源代码（使用 ELK 渲染）如下。请注意，图表中许多明显的属性并未出现在源代码中，例如标签的大小写，因为特殊主题使用了不同的默认值。

<CodeBlock className="language-d2">
    {TerminalTheme}
</CodeBlock>

## 自定义主题

你可以覆写主题值以自定义现有主题，或者完全替换为自己的主题。

这由两个[配置变量](/tour/vars/#configuration-variables)控制：

- `theme-overrides`：替换主题的颜色代码
- `dark-theme-overrides`：替换暗色主题的颜色代码

将以下代码片段添加到上述代码中，将得到如下图表。

```d2-incomplete
vars: {
  d2-config: {
    theme-overrides: {
      B1: "#2E7D32"
      B2: "#66BB6A"
      B3: "#A5D6A7"
      B4: "#C5E1A5"
      B5: "#E6EE9C"
      B6: "#FFF59D"

      AA2: "#0D47A1"
      AA4: "#42A5F5"
      AA5: "#90CAF9"

      AB4: "#F44336"
      AB5: "#FFCDD2"
    }
  }
}
```

<div style={{width: "100%", margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/theme-override.svg2')}}></div>

### 颜色代码

<WebPImage width={700} src={require('@site/static/img/color-code.png').default} webpSrc={require('@site/static/img/color-code.webp').default} alt="D2 color codes"/>

:::info
并非所有颜色代码目前都被使用，但随着 D2 的新功能推出，未来可能会有所改变。
:::
