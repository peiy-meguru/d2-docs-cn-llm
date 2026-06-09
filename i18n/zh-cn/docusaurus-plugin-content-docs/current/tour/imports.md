---
pagination_next: tour/imports-use-cases
---
import CodeBlock from '@theme/CodeBlock';
import ImportsTargeted from '@site/static/d2/imports-targeted.d2';
import People from '@site/static/d2/people.d2';

# 语法（Syntax）

有两种导入方式。以下两个示例结果相同：

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/imports-normal.svg2')}}></div>

> 以下是运行两种导入的结果

在下一节中，我们将看到常见导入用例的示例。

## 两种导入类型

### 1. 常规导入（Regular import）

- `x.d2`
```d2-incomplete
x: {
  shape: circle
}
```
- `y.d2`
```d2-incomplete
a: @x.d2
a -> b
```

这等同于将 `x` 的整个文件作为一个映射（map），作为 `a` 的值。

### 2. 展开导入（Spread import）

- `x.d2`
```d2-incomplete
x: {
  shape: circle
}
```
- `y.d2`
```d2-incomplete
a: {
  ...@x.d2
}
a -> b
```

这告诉 D2 获取文件 `x` 的内容并将其插入到该映射中。

:::info
展开导入仅适用于映射内部。像 `a: ...@x.d2` 这样的用法是无效的。
:::

## 省略扩展名

上面，为了清晰起见，我们写了完整的文件名，但正确的用法是只指定不带后缀的文件名。如果你运行 D2 的自动格式化程序，它会把

```d2-incomplete
x: @x.d2
```

变成

```d2-incomplete
x: @x
```

:::info
D2 不会打开没有 `.d2` 扩展名的文件，这意味着像 `@x.txt` 这样的导入将无法工作。
:::

## 部分导入

你不必导入整个文件。

例如，如果你有一个定义了组织中所有人员的文件，而你只想显示管理者之间的某些关系，你可以导入特定对象。

`donut-flowchart.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsTargeted}
</CodeBlock>

`people.d2`
<CodeBlock className="language-d2-incomplete">
    {People}
</CodeBlock>

:::info
由于 `.` 用于定位，如果你想从文件名中包含 `.` 的文件导入，请使用字符串引号。

`@"schema-v0.1.2"`
:::

### donut-flowchart.d2 的渲染结果

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/imports-targeted.svg2')}}></div>

## 相对导入

相对导入是相对于文件而言的，而不是执行路径。

假设你的工作目录是 `/Users/You/dev`。你的 D2 文件：

- `/Users/you/dev/d2-stuff/x.d2`
```d2-incomplete
y: @../y.d2
```

上述导入将在目录 `/Users/you/dev/` 中搜索 `y.d2`，而不是 `/Users/You`。

:::info
不必要的相对导入会被自动格式化移除。

`@./x` 会被自动格式化为 `@x`。
:::

## 绝对导入

你也可以使用绝对路径进行导入。

```d2-incomplete
# Unix/Linux/Mac
x: @/absolute/path/to/file

# Windows - 由于反斜杠和冒号，必须使用引号
x: @"C:\absolute\path\to\file"
```
