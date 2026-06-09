# 故障排除（Troubleshooting）

* [无法编译某个标签或值](#it-wont-compile-a-specific-label-or-value)
* [文本渲染得太宽/太长](#the-text-is-rendered-too-widelong)
* [连接看起来很杂乱](#connections-look-cluttered)
* [将保留关键字用作普通键](#reserved-keywords-as-regular-keys)
* [我的图表在 Markdown 中包含 HTML 时出错](#my-diagram-is-breaking-with-html-in-markdown)
* [Markdown SVG 在某些 SVG 查看器中无法渲染](#markdown-svgs-wont-render-in-certain-svg-viewers)
* [将 SVG 嵌入 HTML 后没有交互性](#my-svg-isnt-interactive-when-i-embed-into-html)
* [非 ASCII 文本导致问题](#non-ascii-text-breaks-stuff)

## 无法编译某个标签或值

它可能包含一些保留字符，请用 `'` 或 `"` 包裹。

```d2
"x(int y)": "[]int"
'$dollarbills$'
```

## 文本渲染得太宽/太长

添加换行符。

```d2
x: When you go out to buy,\ndon't show your silver.
```

## 连接看起来很杂乱

如果你有一个高度连接的图表，许多连接连接到短标签的形状上，通过手动设置它们的宽度和高度会获得更好的结果。默认情况下，D2 在标签尺寸之外添加最小量的内边距。当一个形状有很多连接时，增加尺寸可以为其提供更多表面积，使连接更美观地布线。

## 将保留关键字用作普通键

如果你想将保留关键字用作键，只需加上引号：

```d2
x: {
  "width": width
}
```

## 我的图表在 Markdown 中包含 HTML 时出错

你的 HTML 必须是语义化的，才能在 SVG XML 中正确解析，例如使用 `<br/>` 而不是 `<br>`。

## Markdown SVG 在某些 SVG 查看器中无法渲染

D2 的 Markdown 支持是通过 xhtml foreignObject 添加的，这意味着 SVG 查看器必须具备 HTML 渲染能力。绝大多数 SVG 查看都支持，但如果你打算在不具备此功能的纯 SVG 编辑器（如 Adobe Illustrator）上使用 D2 图表，则无法正确渲染。

## 将 SVG 嵌入 HTML 后没有交互性

有几种不同的方式将 SVG 嵌入 HTML，各有优劣。如果使用纯 `<img>` 标签，交互性会被阻止。这里有两个很好的资源可以了解更多：

1. 简而言之：
   [https://docs.asciidoctor.org/asciidoc/latest/macros/image-svg/#options-for-svg-images](https://docs.asciidoctor.org/asciidoc/latest/macros/image-svg/#options-for-svg-images)
2. 官方 W3 规范：
   [https://www.w3.org/Graphics/SVG/IG/resources/svgprimer.html#SVG_in_HTML](https://www.w3.org/Graphics/SVG/IG/resources/svgprimer.html#SVG_in_HTML)

## 非 ASCII 文本导致问题

D2 支持任何语言，但有时非 ASCII 字符看起来像保留字符，而实际上并不是。

```d2
hello世界：مرحبا بالعال
```

字符 `：` 与 ASCII 的 `:` 不同，因此不会被视为标签分隔符。对于外语图表，请注意使用特殊字符的 ASCII 版本，如 `:`, `;`, `.` 等。
