---
pagination_next: tour/hello-world
---
# 安装

:::tip
关于 Mac、Windows 和 Linux 的更详细安装说明，请参阅[这里](https://github.com/terrastruct/d2/blob/master/docs/INSTALL.md)。本页是精简版本。
:::

## 安装脚本

推荐的安装方式是运行我们的安装脚本，它会根据你的机器自动确定最佳安装方式。例如，如果 D2 可通过已安装的包管理器获取，它将使用该包管理器。

```shell
# 使用 --dry-run 时，安装脚本会打印将要使用的命令
# 而不会实际安装，以便你了解将要执行的操作。
curl -fsSL https://d2lang.com/install.sh | sh -s -- --dry-run
# 如果一切正常，请执行实际安装。
curl -fsSL https://d2lang.com/install.sh | sh -s --
```

按照指示操作（如有）。运行 `d2 version` 验证安装是否成功。

如果需要卸载：

```shell
curl -fsSL https://d2lang.com/install.sh | sh -s -- --uninstall
```

## 从源码安装

或者，你也可以从源码安装：

```shell
go install oss.terrastruct.com/d2@latest
```


:::info
你也可以在 Github 发布页面下载适用于你操作系统的预编译二进制文件：
[https://github.com/terrastruct/d2/releases](https://github.com/terrastruct/d2/releases)。
:::

# 试一试

```shell
echo 'x -> y' > input.d2
d2 -w input.d2 out.svg
```

它应该会启动一个本地浏览器窗口，当你修改 `input.d2` 时它会自动刷新。在本教程的学习过程中，修改 `input.d2` 以跟随操作。
