import CodeBlock from '@theme/CodeBlock';
import Containers1 from '@site/static/d2/containers-1.d2';
import Containers2 from '@site/static/d2/containers-2.d2';
import Containers3 from '@site/static/d2/containers-3.d2';
import ContainersUnderscore from '@site/static/d2/containers-underscore.d2';

# Containers（容器）

<CodeBlock className="language-d2">
    {Containers1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/containers-1.svg2')}}></div>

## 嵌套语法

你可以通过创建嵌套映射来避免重复书写 container（容器）。

<CodeBlock className="language-d2">
    {Containers2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/containers-2.svg2')}}></div>

## 容器标签

有两种方式定义 container（容器）label（标签）。

### 1. 简写容器标签

```d2-incomplete
gcloud: Google Cloud {
  ...
}
```

### 2. 保留关键字 `label`

```d2-incomplete
gcloud: {
  label: Google Cloud
  ...
}
```

## 示例

<CodeBlock className="language-d2">
    {Containers3}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/containers-3.svg2')}}></div>

## 引用父级

有时你需要从 container（容器）内部引用外部的元素。下划线（`_`）表示 parent（父级）。

<CodeBlock className="language-d2">
    {ContainersUnderscore}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/containers-underscore.svg2')}}></div>
