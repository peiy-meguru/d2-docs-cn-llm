---
pagination_next: tour/exports
---

# CLI 手册

以下是 CLI 的 `man`（手册）副本。它与安装 CLI 后运行 `man d2` 获得的输出一致。

```rolf
d2(1)			    General Commands Manual			 d2(1)

NAME
     d2 – 编译并将 d2 图表渲染为 svg。

SYNOPSIS
     d2 [--watch false] [--theme 0] [--salt string] file.d2
	[file.svg | file.png]
     d2 layout [name]
     d2 fmt file.d2 ...
     d2 play file.d2
     d2 validate file.d2

DESCRIPTION
     d2 编译并将 file.d2 渲染为 file.svg | file.png。

     如果未传递输出路径，则默认为 file.svg。

     传递 - 让 d2 从 stdin 读取或写入 stdout。

     切勿根据输出文件的存在来判断成功与否。请始终使用 d2 的退出
     状态。这是因为有时在渲染过程中发生错误时，d2 仍然会写入部分
     渲染结果，以便在损坏的图表上进行迭代。

     更多文档、源代码和许可证请参见
     https://oss.terrastruct.com/d2。

     托管图标请参见 https://icons.terrastruct.com。

     Playground 运行器请参见 https://play.d2lang.com。

OPTIONS
     -w, --watch false
		 监视输入更改并实时重载。使用 $PORT 和 $HOST 指定
		 监听地址。

     -h, --host localhost
		 与 watch 配合使用时的主机监听地址。

     -p, --port 0
		 与 watch 配合使用时的端口监听地址。

     -t, --theme 0
		 设置图表主题 ID。

     --dark-theme -1
		 当用户的浏览器处于深色模式时使用的主题。当未设置时，
		 --theme 同时用于浅色和深色模式。请注意，D2 代码中设置的
		 显式样式仍会被应用，这可能会产生意外结果。我们计划通过
		 使 D2 中的样式映射特定于浅色/深色模式来解决此问题。
		 请参见 https://github.com/terrastruct/d2/issues/831。

     -s, --sketch false
		 将图表渲染为手绘风格。

     --ascii-mode extended
		 ASCII 输出（.txt 扩展名或 --stdout-format ascii）使用的
		 字符集。选项：standard（基本 ASCII）或 extended（Unicode
		 制表符绘制字符）。

     --center flag
		 将 SVG 居中显示在包含的视口中，例如浏览器屏幕。

     --scale -1  缩放输出。例如，0.5 为默认大小的一半。默认 -1 表示
		 SVG 将适应屏幕，所有其他格式使用默认渲染大小。设置为 1
		 则关闭 SVG 适应屏幕。

     --font-regular
		 用于常规字体的 .ttf 文件路径。如果未提供，使用 Source Sans
		 Pro Regular。

     --font-italic
		 用于斜体字体的 .ttf 文件路径。如果未提供，使用 Source Sans
		 Pro Regular-Italic。

     --font-bold
		 用于粗体字体的 .ttf 文件路径。如果未提供，使用 Source Sans
		 Pro Bold。

     --pad 100	 在渲染图表周围填充的像素数。

     --animate-interval 0
		 如果指定，多个面板将打包为 1 个 SVG，以指定的间隔（毫秒）
		 在每个面板之间切换。只能用于 SVG 和 GIF 导出。

     --browser true
		 watch 打开的浏览器可执行文件。设置为 0 则不打开浏览器。

     -l, --layout dagre
		 将图表布局引擎设置为传递的字符串。可用选项列表请运行
		 layout。

     -b, --bundle true
		 将所有资源和图层打包到输出 svg 中。

     --force-appendix false
		 工具提示和链接的附录会添加到 PNG 导出中，因为 PNG 不支持
		 交互。将此设置为 true 也会为 SVG 导出添加附录。

     --target	 要渲染的目标面板。传递空字符串以定位根面板。如果目标
		 以 '*' 结尾，将渲染其所有场景、步骤和图层。否则，仅渲染
		 目标面板。例如，--target='' 仅渲染根面板，或
		 --target='layers.x.*' 渲染图层 'x' 及其所有子级。

     -d, --debug
		 打印调试日志。

     --img-cache true
		 在监视模式下，图标中使用的图像会被缓存以供后续编译。如果
		 图像可能发生变化，应禁用此选项。

     --timeout 120
		 D2 在超时退出前运行的最大秒数。渲染大型图表时，建议
		 增加此值。

     --check false
		 检查指定文件的格式是否正确。

     --salt string
		 添加盐值以确保输出使用唯一 ID。这在生成多个相同的图表
		 以包含在同一 HTML 文档中时很有用，可以避免重复的 ID 导致
		 无效的 HTML。盐值是一个字符串，将附加到输出中的 ID 后面。

     -h, --help  打印用法信息并退出。

     -v, --version
		 打印版本信息并退出。

     --stdout-format string
		 写入 stdout 时设置输出格式。支持的格式有：png、svg、ascii。
		 仅在输出设置为 stdout (-) 时使用。

     --no-xml-tag false
		 从输出 SVG 文件中省略 XML 标签（<?xml ...?>）。在生成
		 用于直接 HTML 嵌入的 SVG 时很有用。

SUBCOMMANDS
     layout	 列出可用的布局引擎选项及简短帮助。

     layout [name]
		 显示特定布局引擎的详细帮助，包括其配置选项。

     themes	 列出可用的主题。

     fmt file.d2 ...
		 格式化所有传递的文件

     play file.d2
		 在 Playground（在线 Web 查看器）中打开文件
		 (https://play.d2lang.com)

     validate file.d2
		 验证 file.d2

ENVIRONMENT VARIABLES
     许多标志也可以通过环境变量设置。

     D2_WATCH
		 参见 -w[atch] 标志。

     D2_LAYOUT
		 参见 -l[ayout] 标志。

     D2_THEME
		 参见 -t[heme] 标志。

     D2_DARK_THEME
		 参见 --dark-theme 标志。

     D2_PAD  参见 --pad 标志。

     D2_CENTER
		 参见 --center 标志。

     D2_SKETCH
		 参见 -s[ketch] 标志。

     D2_BUNDLE
		 参见 -b[undle] 标志。

     D2_FORCE_APPENDIX
		 参见 --force-appendix 标志。

     D2_FONT_REGULAR
		 参见 --font-regular 标志。

     D2_FONT_ITALIC
		 参见 --font-italic 标志。

     D2_FONT_BOLD
		 参见 --font-bold 标志。

     D2_FONT_SEMIBOLD
		 参见 --font-semibold 标志。

     D2_ANIMATE_INTERVAL
		 参见 --animate-interval 标志。

     D2_TIMEOUT
		 参见 --timeout 标志。

     D2_CHECK
		 参见 --check 标志。

     DEBUG   参见 -d[ebug] 标志。

     IMG_CACHE
		 参见 --img-cache 标志。

     HOST    参见 -h[ost] 标志。

     PORT    参见 -p[ort] 标志。

     BROWSER
		 参见 --browser 标志。

     D2_STDOUT_FORMAT
		 参见 --stdout-format 标志。

     D2_ASCII_MODE
		 参见 --ascii-mode 标志。

     D2_NO_XML_TAG
		 参见 --no-xml-tag 标志。

SEE ALSO
     d2plugin-tala(1)

AUTHORS
     Terrastruct Inc.

macOS 14.1			March 12, 2025			    macOS 14.1
```
