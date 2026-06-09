# 常见问题（FAQ）

* [通用](#general)
  + [这相比 Mermaid、Graphviz、PlantUML 如何？](#how-does-this-compare-to-mermaid-graphviz-plantuml)
  + [这是为小型图表还是复杂图表设计的？](#is-this-designed-for-small-diagrams-or-complex-ones)
  + [D2 CLI 会收集遥测数据吗？](#does-the-d2-cli-collect-telemetry)
  + [D2 需要浏览器才能运行吗？](#does-d2-need-a-browser-to-run)
  + [D2 能在浏览器上运行吗？](#can-d2-run-on-a-browser)
  + [我可以在线使用 D2 吗？](#can-i-use-d2-online)
* [布局](#layouts)
  + [一个对象可以属于多个容器吗？](#can-an-object-be-part-of-more-than-1-container)
  + [我可以指定端口吗？](#can-i-specify-ports)
* [导出](#exports)
  + [SVG 导出没有交互性](#no-interactivity-in-svg-export)

## 通用

### 这相比 Mermaid、Graphviz、PlantUML 如何？

我们创建了一个包含详细比较的网站：[https://text-to-diagram.com](https://text-to-diagram.com)。这是一个社区努力的项目，任何人都可以添加示例、请求更改或比较功能。Mermaid 的维护者也参与了贡献。

### 这是为小型图表还是复杂图表设计的？

两者兼顾。语法保持最小化和非结构化，以尽可能少的行数制作小型图表。同时，该语言包含 IDE 功能，如自动格式化程序、错误消息和注释，以维护大型图表。

然而，它不是为"大数据"设计的。我们不会在数千个节点上测试 D2。

### D2 CLI 会收集遥测数据吗？

不会，D2 在安装后不会使用互联网连接，除了定期检查 GitHub 上的版本更新。

### D2 需要浏览器才能运行吗？

不需要，D2 可以完全在服务器端运行。

### D2 能在浏览器上运行吗？

可以，通过 WebAssembly。D2 通过这种方式在 [https://play.d2lang.com](https://play.d2lang.com) 上运行。我们正在努力将构建包含在发布版本中，并提供说明和示例，以便你可以将其包含在你的浏览器项目中。

### 我可以在线使用 D2 吗？

[https://play.d2lang.com](https://play.d2lang.com)

## 布局

### 一个对象可以属于多个容器吗？

……例如，维恩图中间的一个项目。

目前不支持，近期也不会支持。更多信息请参见[讨论](https://github.com/terrastruct/d2/discussions/328)。

### 我可以指定端口吗？

目前不支持，但近期会支持。更多信息请参见[讨论](https://github.com/terrastruct/d2/discussions/605)。

## 导出

### SVG 导出没有交互性

SVG 导出在使用链接和工具提示时可以具有一些交互元素。但是，SVG 的交互性可能因环境而被禁用。有几种方法可以将 SVG 包含在网页中。

简而言之，当它被当作图像处理时，交互性会丢失。

<table>
  <thead>
    <tr>
      <th>嵌入方式</th>
      <th>链接可点击</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>内联 SVG（&lt;svg&gt;）</td>
      <td>是</td>
    </tr>
    <tr>
      <td>&lt;img&gt; 标签</td>
      <td>否</td>
    </tr>
    <tr>
      <td>&lt;object&gt; 标签</td>
      <td>是</td>
    </tr>
    <tr>
      <td>&lt;iframe&gt; 标签</td>
      <td>是</td>
    </tr>
    <tr>
      <td>CSS 背景图片</td>
      <td>否</td>
    </tr>
    <tr>
      <td>&lt;embed&gt; 标签</td>
      <td>是</td>
    </tr>
  </tbody>
</table>
