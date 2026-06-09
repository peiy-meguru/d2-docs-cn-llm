import CodeBlock from '@theme/CodeBlock';
import StyleClasses1 from '@site/static/d2/style-classes-1.d2';
import StyleClasses2 from '@site/static/d2/style-classes-2.d2';
import MultipleClasses from '@site/static/d2/multiple-classes.d2';
import OrderedClasses from '@site/static/d2/ordered-classes.d2';

# 类（Classes）

类可以将属性聚合在一起，并重复使用。

<CodeBlock className="language-d2">
    {StyleClasses1}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/style-classes-1.svg2')}}></div>

## 连接类（Connection classes）

作为 D2 语法的提醒，你可以在初始声明时以及之后将类应用于连接。

初始声明时：

```d2
a -> b: {class: something}
```

定位时：

```d2
a -> b
# ...
(a -> b)[0].class: something
```

## 覆写类（Overriding classes）

如果你的对象定义了类也定义的属性，那么对象的属性会覆盖类的属性。

<CodeBlock className="language-d2">
    {StyleClasses2}
</CodeBlock>

<div style={{width: 100, margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/style-classes-2.svg2')}}></div>

## 多个类

你也可以使用数组作为值来应用多个类。

<CodeBlock className="language-d2">
    {MultipleClasses}
</CodeBlock>

<div style={{width: 200, margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/multiple-classes.svg2')}}></div>

### 顺序重要

当指定多个类时，它们从左到右依次应用。

<CodeBlock className="language-d2">
    {OrderedClasses}
</CodeBlock>

<div style={{width: 200, margin: "0 auto"}} className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/ordered-classes.svg2')}}></div>

## 进阶：将类用作标签

如果你想对 D2 图表进行后处理，你也可以使用类来任意标记对象。你应用的任何 `class` 都会被写入 SVG 元素作为 `class` 属性。例如，你可以在嵌入 D2 SVG 的网页上应用自定义 CSS，如 `.stuff { ... }`（或使用 Javascript 进行 onclick 处理等）。
