---
pagination_next: tour/modular-classes
---
import CodeBlock from '@theme/CodeBlock';
import Models from '@site/static/d2/models.d2';
import ImportsMVAccessView from '@site/static/d2/imports-mv-access-view.d2';
import ImportsMVSSHView from '@site/static/d2/imports-mv-ssh-view.d2';

# 模型-视图（Model-view）

一种流行的模式是一次性定义你的模型，然后在多个不同视图中重用。

## `models.d2`
<CodeBlock className="language-d2-incomplete">
    {Models}
</CodeBlock>

## `access-view.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsMVAccessView}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/imports-mv-access-view.svg2')}}></div>

## `ssh-view.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsMVSSHView}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/imports-mv-ssh-view.svg2')}}></div>
