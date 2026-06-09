import CodeBlock from '@theme/CodeBlock';
import Cat from '@site/static/bespoke-d2/cat.d2';
import LOTR from '@site/static/bespoke-d2/lotr.d2';

# 面板间链接（Linking between boards）

我们之前介绍过 `link` 是跳转到外部资源的方式。它们也可以用来创建跳转到其他面板的交互功能。我们称之为"内部链接"。

内部链接示例：

<CodeBlock className="language-d2-incomplete">
    {Cat}
</CodeBlock>

<embed src={require('@site/static/img/generated/cat.pdf').default} width="100%" height="800"
 type="application/pdf" />

:::info
如果你的面板名称包含 `.`，请使用引号来定位该面板。
例如：

```d2-incomplete
a.link: layers."2012.06"

layers: {
  "2012.06": {
    hello
  }
}
```
:::

## 父级引用

下划线 `_` 用于引用父作用域，但在 `link` 值中使用时，它们引用的不是父容器，而是父面板。

<CodeBlock className="language-d2-incomplete">
    {LOTR}
</CodeBlock>

<embed src={require('@site/static/img/generated/lotr.pdf').default} width="100%" height="800"
 type="application/pdf" />

## 反向链接

注意顶部的导航栏是可点击的。你可以通过点击文本来轻松返回根面板或任何祖先面板。
