import CodeBlock from '@theme/CodeBlock';
import ImportsTemplate from '@site/static/d2/imports-template.d2';
import ImportsWrapperTemplate from '@site/static/d2/imports-wrapper-template.d2';

# 模板（Template）

你为外部咨询客户制作图表。为了显得更专业，所有图表必须包含在你的设计师创建的、符合品牌形象的模板中。

- `diagram.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsTemplate}
</CodeBlock>

- `wrapper-template.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsWrapperTemplate}
</CodeBlock>

:::info
当 D2 完成 glob（`*`）支持后，这个用例将变得更加强大。
:::

## `diagram.d2` 的渲染结果

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/imports-template.svg2')}}></div>
