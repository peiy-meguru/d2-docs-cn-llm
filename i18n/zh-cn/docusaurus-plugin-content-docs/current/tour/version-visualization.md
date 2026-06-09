---
pagination_next: tour/imported-template
---
import CodeBlock from '@theme/CodeBlock';
import ImportsVVHistory from '@site/static/d2/imports-vv-history.d2';
import UsersCurrent from '@site/static/d2/users-current.d2';
import UsersV01 from '@site/static/d2/users-v0.1.d2';

# 版本可视化（Version visualization）

## 历史（History）

你想了解系统的架构（schema）如何随时间演变。只要图表通过导入实现了模块化，这种可视化就很容易实现。

- `history.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsVVHistory}
</CodeBlock>

- `users.d2`（最新版本 0.2）
<CodeBlock className="language-d2-incomplete">
    {UsersCurrent}
</CodeBlock>

- `users.d2`（0.1 版本）
<CodeBlock className="language-d2-incomplete">
    {UsersV01}
</CodeBlock>

要查看 `users.d2` 在 `v0.1` 时的样子，你可以使用 `git` 获取该版本：

```sh
cp users.d2 users-current.d2
git checkout tags/v0.1 users.d2
mv users.d2 users-v0.1.d2
```

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/imports-vv-history.svg2')}}></div>

## 比较（Compare）

你是苹果公司的经理，有两个团队秘密地在同一个产品上工作了多年。经过多年在各自孤岛中的迭代，你成立了一个委员会来比较两个结果。评估从在一间门窗紧闭的暗室里投射总览图、比较他们的设计决策开始。

- `compare.d2`
```d2-incomplete
Team Alpha: {
  Quick facts: |md
    - 3 名 L6 工程师
  |
  Schema: {
    ...@alpha-schema
  }
  API: {
    ...@alpha-api
  }
  # 等等
}

Team Charlie: {
  Quick facts: |md
    - 2 名 L5
    - 5 名 L4
    - 15 名 L3
  |
  Schema: {
    ...@charlie-schema
  }
  API: {
    ...@charlie-api
  }
  # 等等
}
```

然后从不同仓库检出相应的图表。
```sh
gh repo clone apple/team-alpha
gh repo clone apple/team-charlie

cp apple/team-alpha/schema.d2 alpha-schema.d2
cp apple/team-charlie/schema.d2 charlie-schema.d2

cp apple/team-alpha/api.d2 alpha-api.d2
cp apple/team-charlie/api.d2 charlie-api.d2
```

渲染后的图表留给读者作为练习。
