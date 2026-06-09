# ELK

**[🔗 示例](/examples/elk)**

ELK 是一个成熟的层次化布局引擎，由[基尔克里斯蒂安阿尔布莱希特大学](https://www.rtsys.informatik.uni-kiel.de/en/team)的一个学术研究小组积极维护。

## 参考

[https://www.eclipse.org/elk/reference.html](https://www.eclipse.org/elk/reference.html)

## 优点

- 清晰、正交的路由。
- 高度可定制。
- 快速。
- 擅长最小化交叉。
- 原生支持容器到容器的路由，比 dagre 处理得更好。
- 持续改进，定期发布新版本。
- 为 SQL 表路由精确到具体列。

## 缺点

- 严格层次化，与 dagre 一样。
- 某些路由有不必要的弯曲。
- 对对称性的考虑极少。
