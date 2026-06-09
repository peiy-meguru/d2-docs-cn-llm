# 字体（Fonts）

D2 使用 4 种字体系列：

- [Source Sans Pro](https://fonts.google.com/specimen/Source+Sans+Pro) 用于大部分文本，包括标签、Markdown 等。
- [Source Code Pro](https://fonts.google.com/specimen/Source+Code+Pro) 用于代码块和 Class 形状中的文本。
- [Architect's Daughter](https://fonts.google.com/specimen/Architects+Daughter) 和 [Fuzzy Bubbles](https://fonts.google.com/specimen/Fuzzy+Bubbles) 的混合体，用于 `sketch` 模式下的文本。

目前在 CLI 上，你可以通过以下标志用自定义的 TTF 文件替换 Source Sans Pro：

- `--font-regular`
- `--font-italic`
- `--font-bold`
- `--font-semibold`

这些应指向一个 `.ttf` 文件，例如：

```shell
d2 --font-regular=./helvetica-regular.ttf input.d2
```

建议要么不提供任何字体，要么提供所有字体，以保持一致性。如果你只提供部分字体，缺失的样式将回退到 Source Sans Pro。例如，如果你提供了 `--font-regular`、`--font-bold` 和 `--font-semibold`，那么斜体将保持为 Source Sans Pro Italic。

## 等宽字体（Mono fonts）

如果你想自定义等宽字体：

- `--font-regular`
- `--font-italic`
- `--font-bold`
- `--font-semibold`

## 草图字体（Sketch font）

在草图模式下，如果你提供了字体，它将替换默认的手绘字体系列，而不是 Source Sans Pro。
