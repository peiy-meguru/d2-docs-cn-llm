import CodeBlock from '@theme/CodeBlock';
import ImportsNested from '@site/static/bespoke-d2/imports-nested.d2';
import ServiceB from '@site/static/bespoke-d2/serviceB.d2';
import Data from '@site/static/bespoke-d2/data.d2';

# 嵌套组合（Nested composition）

导入使大型组合更易于管理。

像那些带你从高层概览到低层细节的大型图表，现在可以清晰构建。

渲染 `overview.d2` 会给我们一个嵌套图表，同时每个文件保持简洁和可读。

### `overview.d2`
<CodeBlock className="language-d2-incomplete">
    {ImportsNested}
</CodeBlock>

### `serviceB.d2`
<CodeBlock className="language-d2-incomplete">
    {ServiceB}
</CodeBlock>

### `data.d2`
<CodeBlock className="language-d2-incomplete">
    {Data}
</CodeBlock>

## `overview.d2` 的渲染结果

<embed src={require('@site/static/img/generated/imports-nested.pdf').default} width="100%" height="800"
 type="application/pdf" />
