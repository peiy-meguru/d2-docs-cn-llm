---
pagination_next: tour/elk
---

# Dagre

**[🔗 示例](/examples/dagre)**

Dagre 是 D2 的默认布局引擎。

## 参考

[https://github.com/dagrejs/dagre](https://github.com/dagrejs/dagre)

## 优点

- 非常快。
- 经过实战检验（得益于 MermaidJS，它专门使用 Dagre 来生成流程图）。
- 通常效果不错。
- 算法背后的理论是支撑 Graphviz 的论文。
- 层次化布局渲染效果很好。

## 缺点

- 不再维护。开发已于 2018 年停止。
- 偶尔会做出一些难以解释的边路由决策（[https://github.com/dagrejs/dagre/issues/256](https://github.com/dagrejs/dagre/issues/256)）。
- 布局算法严格来说是层次化的，即使底层图表不是层次化的。
- dagre 本身不支持容器对另一个容器（或另一个容器子元素）的连接。D2 添加了一个 shim 来使其工作，但由于 shim 的存在，一些核心算法考虑因素会丢失。
- 多段边路由是曲线而非正交线，可能导致不美观的曲线。
