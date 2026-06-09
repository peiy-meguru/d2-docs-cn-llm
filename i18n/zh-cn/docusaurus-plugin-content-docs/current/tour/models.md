import CodeBlock from '@theme/CodeBlock';
import Suspend from '@site/static/d2/suspend.d2';
import Suspend2 from '@site/static/d2/suspend-2.d2';
import Suspend3 from '@site/static/d2/suspend-3.d2';
import Suspend4 from '@site/static/d2/suspend-4.d2';

# 模型（Models）

假设你想一次性定义所有模型和模型之间的关系，然后以不同方式展示它们。

首先，定义模型和关系。

<CodeBlock className="language-d2-incomplete">
    {Suspend}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/suspend.svg2')}}></div>

我们将以此作为同一模型多视图的示例。如何将这些视为模型而不仅仅是普通的形状和连接？我们使用以下关键字：

1. `suspend`（挂起）：标记形状或连接以进行删除
2. `unsuspend`（恢复）：恢复形状或连接

由于模型在使用前应保持不可见，我们在图表顶部定义模型，并使用以下 globs 将所有模型 `suspend`。

```d2
**: suspend
(** -> **)[*]: suspend
```

然后我们使用 globs 选择性地 `unsuspend` 想要显示的模型。让我们看一些用例。

:::info
如果你还没有，请先熟悉 [globs](globs.md)。
:::

## 仅显示顶层

<CodeBlock className="language-d2-incomplete">
    {Suspend2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/suspend-2.svg2')}}></div>

## 仅显示与 X 的连接

<CodeBlock className="language-d2-incomplete">
    {Suspend3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/suspend-3.svg2')}}></div>

## 仅显示点赞

<CodeBlock className="language-d2-incomplete">
    {Suspend4}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/suspend-4.svg2')}}></div>

## 利用导入

你可能已经注意到，每个示例都重复了初始模型。你可以进一步应用"单一模型"原则，将模型定义在单独的文件中并导入。更多信息请参阅[导入模型-视图模式](/tour/model-view/)。
