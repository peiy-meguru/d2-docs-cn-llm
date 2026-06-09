# 自动格式化（Autoformat）

你几乎不需要考虑缩进、换行、连字符数量或间距等样式决策。D2 的自动格式化程序会在编译时自动格式化你的 D2 文件，轻松保持所有声明的一致性和可读性。

如果你的文件是

```d2
aws_s3:    AWS S3 California{
  Monitoring ---------->California
}
```

编译时会变成

```d2
aws_s3: AWS S3 California {
  Monitoring -> California
}
```

## 运行格式化程序

如果你使用 `d2` CLI，可以通过以下命令对文件运行格式化程序：

```sh
d2 fmt file.d2
```

格式化程序旨在集成到插件和扩展中，在文件写入时自动调用格式化功能。此功能取决于具体插件。
