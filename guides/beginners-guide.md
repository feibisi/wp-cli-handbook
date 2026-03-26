---
title: "新手入门指南"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Guides
    - Repos
    - Data
---

# 新手入门指南

听说 WP-CLI 想尝试却不知从何入手？这份指南正是为你准备的。无需任何编程经验！

本指南建议从头至尾顺序阅读。每个章节都建立在前文基础上，将带你从初次打开终端开始，逐步完成首次 WP-CLI 命令操作，并学会在需要时获取帮助。

## 什么是命令行？

当你使用电脑时，通常通过点击图标、按钮和菜单来与之交互。这被称为**图形用户界面（GUI）**。

**命令行**（也称为终端、Shell 或控制台）是与计算机交互的另一种方式。你无需点击，而是输入文本命令并按 **Enter** 键来执行它们。起初它可能看起来令人生畏，但这实际上只是告诉计算机该做什么的另一种方式。

### 打开终端

**在 macOS 上：**

1.  按下 **Command (⌘) + 空格键** 打开 Spotlight 搜索。
2.  输入 `Terminal` 并按 **Enter** 键。
3.  一个带有黑色或白色背景和闪烁光标的窗口会出现。这就是终端！

**在 Windows 上：**

1.  按下 **Windows 键 + R** 打开“运行”对话框。
2.  输入 `cmd` 并按 **Enter** 键。
3.  或者，在开始菜单中搜索“命令提示符”或“PowerShell”。

> **给 Windows 用户的提示：** WP-CLI 在 Git Bash 或 Windows Subsystem for Linux (WSL) 中运行效果最佳。你可以从 [git-scm.com](https://git-scm.com/downloads) 下载 Git Bash。

**在 Linux 上：**

1.  在应用程序菜单中查找“终端”，或者在许多发行版上按 **Ctrl + Alt + T**。

### 基础终端导航

打开终端后，以下是几个需要了解的基本命令：

| 命令 | 功能 |
|---------|-------------|
| `pwd` | 显示你当前所在的文件夹 |
| `ls` (macOS/Linux) 或 `dir` (Windows) | 列出当前文件夹中的文件和文件夹 |
| `cd folder-name` | 进入名为 `folder-name` 的文件夹 |
| `cd ..` | 返回上一级文件夹 |
| `clear` | 清空终端屏幕 |

别担心——你现在不需要记住所有这些。需要时，随时可以回来查看这个表格。

## 什么是 WP-CLI？

WP-CLI 是 **WordPress 的命令行界面**。它允许你在终端中输入命令来管理你的 WordPress 网站，而无需在 WordPress 管理后台中点击操作。

可以这样理解：任何你可以在 WordPress 后台完成的操作（安装插件、创建用户、更新设置），你都可以使用 WP-CLI 来完成——而且通常速度更快。

### 为何要使用 WP-CLI？

以下是非技术型 WordPress 用户也觉得 WP-CLI 实用的几个原因：

- **速度：** 用一条命令更新所有插件，无需逐个点击。
- **自动化：** 轻松重复相同任务，无需每次都进入管理后台。
- **批量操作：** 一次性处理大量文章、用户或设置项。
- **远程管理：** 无需打开浏览器即可管理远程服务器上的网站。
- **可靠性：** 减少点击意味着降低出错概率。

## 安装 WP-CLI

关于在 macOS、Linux 和 Windows 上的分步安装说明，请参阅[安装指南](https://make.wordpress.org/cli/handbook/guides/installing/)。它涵盖了系统要求、推荐的 Phar 下载方法以及 Composer 和 Homebrew 等替代安装选项。

## 运行 WP-CLI：在 WordPress 文件夹内与外的区别

WP-CLI 需要知道要操作哪个 WordPress 安装。默认情况下，它会在你的**当前目录**（终端当前所在的文件夹）中查找 WordPress。

这意味着你通常需要在运行 WP-CLI 命令前，先 `cd` 进入你的 WordPress 站点文件夹。例如：

```
cd /var/www/mysite
wp plugin list
```

如果你从一个不包含 WordPress 安装的文件夹运行 `wp plugin list`，你会收到类似这样的错误：

```
Error: This does not seem to be a WordPress installation.
```

**我的 WordPress 文件夹在哪里？**

- 在典型的共享主机上，通常是类似 `/home/username/public_html` 或 `/var/www/html` 的路径。
- 如果你使用 Local、MAMP 或 XAMPP 等本地开发工具，每个工具都有自己的文件夹结构——请查阅其文档。
- 在托管的 WordPress 主机上，WP-CLI 可能已预先配置好，无需先执行 `cd` 命令即可工作。

## 运行你的第一个 WP-CLI 命令

在终端中导航到你的 WordPress 文件夹（参见[上文](#在-wordpress-文件夹内外运行-wp-cli)）。例如：

```
cd /var/www/mysite
```

然后尝试运行这个命令：

```
wp --info
```

这将显示关于你的 WP-CLI 安装的信息。如果它正常运行，你就可以开始了！

要查看已安装的 WordPress 版本：

```
wp core version
```

要列出你站点上的插件：

```
wp plugin list
```

## 阅读 WP-CLI 输出

当您运行 WP-CLI 命令时，它会在终端中打印响应。以下是常见消息的含义：

- **`Success:`** — 命令按预期执行成功。
- **`Warning:`** — 命令已运行，但存在需要注意的情况。
- **`Error:`** — 出现错误。请阅读消息以了解详情。

## 获取帮助

### 内置帮助

WP-CLI 为每个命令都内置了文档。如果遇到问题，可以运行 `wp help` 来查看所有可用命令的列表：

```
wp help
```

要获取特定命令的帮助，请在 `help` 后加上命令名称。例如：

```
wp help plugin
wp help plugin install
```

### 社区支持

如果内置帮助不够用，这些资源可以提供帮助：

- **[WP-CLI 手册](https://make.wordpress.org/cli/handbook/)** — 完整的参考文档。
- **[GitHub Issues](https://github.com/wp-cli/wp-cli/issues)** — 报告错误或搜索已知问题。
- **[WordPress.org 支持论坛](https://wordpress.org/support/)** — 来自社区的通用 WordPress 帮助。

## 在远程服务器上使用 WP-CLI（SSH）

如果你的 WordPress 站点托管在远程服务器上（大多数生产环境网站都是如此），你仍然可以使用 WP-CLI。有两种常见方法：

1.  **通过 SSH 登录服务器并在其中运行 WP-CLI。** 大多数主机提供商都提供 SSH 访问权限。使用类似以下命令连接：

    ```
    ssh username@yoursite.com
    ```

    然后导航到你的 WordPress 文件夹并正常使用 WP-CLI。

2.  **使用 WP-CLI 内置的 SSH 支持。** WP-CLI 可以直接从你的本地机器在远程服务器上运行命令。详情请参阅[远程运行命令](https://make.wordpress.org/cli/handbook/guides/running-commands-remotely/)指南。

## 深入学习

掌握了基础知识后，以下是很好的下一步学习资源：

- **[WP-CLI 常见任务](https://make.wordpress.org/cli/handbook/guides/common-tasks/)** — 日常 WordPress 管理的实用示例。
- **[快速入门指南](https://make.wordpress.org/cli/handbook/guides/quick-start/)** — 包含更多示例的 WP-CLI 简短教程。
- **[远程运行命令](https://make.wordpress.org/cli/handbook/guides/running-commands-remotely/)** — 通过 SSH 管理线上网站服务器。
- **[所有 WP-CLI 命令](https://developer.wordpress.org/cli/commands/)** — 可用命令的完整列表。
- **[外部资源](https://make.wordpress.org/cli/handbook/guides/external-resources/)** — WP-CLI 用户的博客文章、幻灯片和视频。

你无需一次性学会所有内容。从你想加速完成的任务开始，找到合适的命令，然后逐步深入！