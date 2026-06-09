---
pagination_next: tour/comments
---
import CodeBlock from '@theme/CodeBlock';
import Strings2 from '@site/static/d2/strings-2.d2';

# 字符串（Strings）

## 无引号字符串

你可能已经注意到，到目前为止的示例都没有使用引号。我们的目标是让 D2 易于使用，而引号往往会妨碍这一点。

引号在多个方面增加阻力。首先，你必须闭合已打开的引号。其次，你必须记住是使用单引号还是双引号。最后，它们会增加语法噪音。

这意味着大多数情况下，无需担心引号！

前导和尾随空白字符会被修剪。

```d2
   Office Bulb   :     Philips
            Switch   ->   Office Bulb
```

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/strings-1.svg2')}}></div>

无引号字符串不能包含语言中其他地方使用的某些字符。语法高亮会清晰地提示你是否使用了禁止符号。

## 带引号字符串

如果你需要使用这些符号，可以使用单引号或双引号字符串：

<CodeBlock className="language-d2">
    {Strings2}
</CodeBlock>

<div className="embedSVG" dangerouslySetInnerHTML={{__html: require('@site/static/img/generated/strings-2.svg2')}}></div>

:::info
如果文本中包含单引号，则应使用双引号，反之亦然。如果同时包含两者，请使用双引号并像在其他语言中一样使用 `\` 转义。
:::

## 自动格式化

如果你的块字符串缩进不足，自动格式化程序会纠正它。

```d2
parent: {
example_code: |go
  package fs

  type FS interface {
    Open(name string) (File, error)
  }

  type File interface {
    Stat() (FileInfo, error)
    Read([]byte) (int, error)
    Close() error
  }

  var (
    ErrInvalid    = errInvalid()    // "invalid argument"
    ErrPermission = errPermission() // "permission denied"
    ErrExist      = errExist()      // "file already exists"
    ErrNotExist   = errNotExist()   // "file does not exist"
    ErrClosed     = errClosed()     // "file already closed"
  )
|
}
```

将变为：

```d2
parent: {
  example_code: |go
    package fs

    type FS interface {
      Open(name string) (File, error)
    }

    type File interface {
      Stat() (FileInfo, error)
      Read([]byte) (int, error)
      Close() error
    }

    var (
      ErrInvalid    = errInvalid()    // "invalid argument"
      ErrPermission = errPermission() // "permission denied"
      ErrExist      = errExist()      // "file already exists"
      ErrNotExist   = errNotExist()   // "file does not exist"
      ErrClosed     = errClosed()     // "file already closed"
    )
  |
}
```

自动格式化程序会检查是否存在任何非空行缩进不足。如果是，所有行都会被添加正确的缩进量（同时保留现有的公共缩进）。这样你就不必在编辑器中调整缩进了。只需在块字符串起始后的第一列粘贴任何代码，自动格式化程序就会为你纠正。

在缩进到基础块字符串缩进（两个空格）后，你可以使用制表符来缩进块字符串。基础块字符串缩进中的任何制表符都会被自动转换为两个空格。
