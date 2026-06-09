# TALA

**[🔗 示例](/examples/tala)**

由 Terrastruct 开发的专有布局引擎，专为软件架构图设计。

TALA 是独立于 D2 安装的，以保持 100% 免费开源的 D2 与专有闭源的 TALA 之间的清晰界限。你可以在此处下载：[https://github.com/terrastruct/tala](https://github.com/terrastruct/tala#installation)。

## 参考

[https://terrastruct.com/tala/](https://terrastruct.com/tala/)

最新的信息，请参阅[官方 TALA 手册](https://github.com/terrastruct/TALA/blob/master/TALA_User_Manual.pdf)。

## 优点

- 作为一个通用的正交布局引擎，TALA 不受限于单一类型（如层次、树状或放射状）。对于从根本上非层次化的布局，TALA 可以产生像人类在白板上绘制一样的图表。
- 可以使用 `top` 和 `left` 锁定位置。
- 考虑并偏好对称性。
- 对容器有一流的支持。
- `direction` 可以按容器设置。
- `near` 可以指定为指向另一个形状。
- `sql_table` 连接精确指向对应行。
- 动态标签定位以避免遮挡。
- 网格单元格的连接使用 TALA 的路由引擎，而非始终使用直线。

## 缺点

- 不是免费的。
- 相对较新。与已有 10 年以上历史的替代布局引擎相比，TALA 投入生产仅约 2 年。
- 比其他布局引擎更具随机性。标签的微小更改可能会级联成完全不同的布局。
