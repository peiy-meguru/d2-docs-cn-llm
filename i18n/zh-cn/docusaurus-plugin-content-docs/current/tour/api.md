---
pagination_next: tour/man
---

# D2 Oracle

D2 在 AST 之上构建了一个 API，用于**在 Go 中以编程方式创建图表**。
该包为 `d2/d2oracle`。

Terrastruct 大量使用此 API 来实现[双向编辑](https://youtu.be/EhxVVkxv2Ns?t=150)。我们有这些函数的[全面测试覆盖](https://github.com/terrastruct/d2/blob/master/d2oracle/edit_test.go)。如果您对文档有任何疑问，几乎一定有一个可以解答您问题的测试。（我们也乐意提供帮助，只需提交 GitHub issue！）

关于详细介绍示例用法（构建 SQL 表图）的博客文章，请参阅 [https://terrastruct.com/blog/post/generate-diagrams-programmatically/](https://terrastruct.com/blog/post/generate-diagrams-programmatically/)。

:::info 无修改
`d2oracle` 中的所有函数都是纯函数：它们不会修改原始图，而是返回一个新图。如果你链式调用，不要忘记使用前一次调用返回的结果图。
:::

## Create（创建）

创建一个图形（shape）或连接（connection）。

```go
func Create(g *d2graph.Graph, boardPath []string, key string) (newG *d2graph.Graph, newKey string, _ error)
```

**参数**：
- `g`：D2 图
- `boardPath（面板路径）`：要修改的面板路径。仅适用于多面板图；
  否则传入 `nil`。
- `key（键）`：正在创建的图形或连接的 ID

**返回值**：
- `newG`：修改后的 D2 图
- `newKey`：创建的图形或连接的实际 ID

在给定的 `key（键）`中指定的所有内容都将被创建。例如，
如果在两个不存在的图形之间创建连接，它们将在同一次调用中被
创建。如果指定了一个嵌套对象，它将创建父容器（如果它们不存在的话）。

```go
// 此调用创建 6 个图形和 1 个连接
d2oracle.Create(g, nil, "a.b.c -> x.y.z")
```

如果使用相同的图形 ID 两次调用 `Create（创建）`，将会收到
错误。如果使用相同的边 ID 两次调用，将会创建另一条边。

`newKey` 是所创建对象的 ID。这并不总是与输入的 key 匹配。

对于图形，可能会发生 ID 冲突。`Create（创建）`在此情况下会附加一个计数器。
```go
// newKey = "a"
g, newKey, _ = d2oracle.Create(g, nil, "a")
// newKey = "a 2"
_, newKey, _ = d2oracle.Create(g, nil, "a")
```


连接 ID 包含索引。
```go
// newKey = "(a -> b[0])"
g, newKey, _ = d2oracle.Create(g, nil, "a -> b")
// newKey = "(a -> b[1])"
_, newKey, _ = d2oracle.Create(g, nil, "a -> b")
```

如果你有如下的多面板图：

```d2-incomplete
x

layers: {
  y: {}
}
```

```go
// 在根层级创建图形 "a"
g, _ = d2oracle.Create(g, nil, "a")
// 在图层 "y" 中创建图形 "a"
g, _ = d2oracle.Create(g, []string{"y"}, "a")
```

## Set（设置）

设置图形或连接的属性。

```go
func Set(g *d2graph.Graph, boardPath []string, key string, tag, value *string) (newG *d2graph.Graph, _ error)
```

**参数**：
- `g`：D2 图
- `boardPath（面板路径）`：要修改的面板路径。仅适用于多面板图；
  否则传入 `nil`。
- `key（键）`：属性的标识符
- `tag（标签）`：语言标签。仅在设置可以不同语言的文本值时为非空，
  例如代码片段值。
- `value（值）`：正在设置的值

**返回值**：
- `newG`：修改后的 D2 图

正在 `Set（设置）`的图形或连接必须存在。

```go
g, _, _ := d2oracle.Create(g, "a")
g, _ = d2oracle.Set(g, "a.style.fill", nil, "red")
```

如果属性已经设置，它将被覆盖。

```go
// D2 graph: "a.style.fill: red"
g, _ = d2oracle.Set(g, "a.style.fill", nil, "red")
// D2 graph: "a.style.fill: blue"
g, _ = d2oracle.Set(g, "a.style.fill", nil, "blue")
```

连接通过索引定位。

```go
// 设置第一个连接的标签
g, _ = d2oracle.Set(g, "(a -> b)[0].style.label", nil, "uno")
// 设置第二个连接的标签
g, _ = d2oracle.Set(g, "(a -> b)[1].style.label", nil, "dos")
```

要取消设置属性，只需传入 `nil`。

```go
g, _ = d2oracle.Set(g, "a.style.fill", nil, nil)
g, _ = d2oracle.Set(g, "(a -> b)[0].style.label", nil, nil)
```

如果不传入属性而只传入图形或连接的 ID，它将设置
该对象的主要值（通常是标签）。

```go
// 将 `a` 的标签设置为 Markdown 文本
g, _ = d2oracle.Set(g, "a", "md", "# I am A")
```



## Delete（删除）

删除一个图形或连接。

```go
func Delete(g *d2graph.Graph, boardPath []string, key string) (newG *d2graph.Graph, _ error)
```

**参数**：
- `g`：D2 图
- `boardPath（面板路径）`：要修改的面板路径。仅适用于多面板图；
  否则传入 `nil`。
- `key（键）`：图形或连接的标识符

**返回值**：
- `newG`：修改后的 D2 图

如果指定一个有子级的容器，这些子级也会被删除。

```go
g, _, _ := d2oracle.Create(g, "a.b")
// `a.b` 也会被删除
g, _ = d2oracle.Delete(g, "a")
```

## Rename（重命名）

重命名图形或连接的 ID。

:::info
注意，ID 不等于标签。如果想更改标签，请使用 `Set（设置）`。
:::

```go
func Rename(g *d2graph.Graph, boardPath []string, key, newName string) (newG *d2graph.Graph, err error)
```

**参数**：
- `g`：D2 图
- `boardPath（面板路径）`：要修改的面板路径。仅适用于多面板图；
  否则传入 `nil`。
- `key（键）`：图形或连接的当前标识符
- `newName`：图形或连接的新标识符

**返回值**：
- `newG`：修改后的 D2 图

Rename（重命名）将重命名给定 key 的所有引用。

```go
g, _, _ := d2oracle.Create(g, "a.b -> a.c")
// New D2: `z.b -> z.c`
g, _ = d2oracle.Rename(g, "a", "z")
```

## Move（移动）

将给定的图形或连接移动到另一个容器。

```go
func Move(g *d2graph.Graph, boardPath []string, key, newKey string) (newG *d2graph.Graph, err error)
```

:::info
如果提供两个相同作用域的键（例如 "a" 到 "b"），这与 `Rename（重命名）`相同。
:::

**参数**：
- `g`：D2 图
- `boardPath（面板路径）`：要修改的面板路径。仅适用于多面板图；
  否则传入 `nil`。
- `key（键）`：图形或连接的当前标识符
- `newKey`：图形或连接的新标识符

**返回值**：
- `newG`：修改后的 D2 图

你可以将对象移出容器、移入容器或在容器间移动。

```go
g, _, _ := d2oracle.Create(g, "a.b.c -> x.y.z")
// 将 c 从 b 移出到 a
g, _ = d2oracle.Move(g, "a.b.c", "a.c")
// 将 c 移回 b
g, _ = d2oracle.Move(g, "a.c", "a.b.c")
// 将 c 移入 x.y.z
g, _ = d2oracle.Move(g, "a.b.c", "x.y.z.c")
```

## ID Deltas（ID 增量）

对于可能影响多个 ID 的调用，存在一个 API 可以获取每个 ID 更改的映射。
这可能很难追踪；例如，如果你移动一个包含许多子级的容器，
所有这些子级的 ID 以及引用容器内任何内容的所有连接都会发生变化。

什么时候会用到这个？如果你在图形之外的其他地方（例如
你自己的存储中或写回到某个地方）维护 D2 对象的状态，
应该使用这些调用来跟踪所有程序化更改。

Delta（增量）方法：
- MoveIDDeltas（移动 ID 增量）
- DeleteIDDeltas（删除 ID 增量）
- RenameIDDeltas（重命名 ID 增量）

这些方法都具有与其对应方法相同的输入参数，并返回一个字符串到
字符串的 ID 更改映射。

给定以下 D2 脚本输入：
```d2
x
y
x -> z
```

`deltas, err := MoveIDDeltas(g, nil, "x", "y.x")`

`deltas`：
```json
{
  "(x -> z)[0]": "(y.x -> z)[0]",
  "x": "y.x"
}
```
