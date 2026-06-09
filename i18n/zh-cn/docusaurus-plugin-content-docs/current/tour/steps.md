import CodeBlock from '@theme/CodeBlock';
import Chicken from '@site/static/bespoke-d2/chicken.d2';

# 步骤（Steps）

"步骤"（Step）代表事件序列中的一个步骤。

每个步骤都继承自其前一个步骤。第一步继承自其父级，无论是场景还是图层。

注意，例如在步骤 3 中，对象"Approach road"即使没有定义也存在，因为它是从步骤 2 继承的，而步骤 2 又是从步骤 1 继承的。

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/chicken.svg2')}}></div>

<CodeBlock className="language-d2-incomplete">
    {Chicken}
</CodeBlock>
