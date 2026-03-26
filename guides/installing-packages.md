---
title: "安装 WP-CLI 包"
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

# 安装 WP-CLI 包

WP-CLI 包是基于 WP-CLI 构建的社区维护项目。它们可以包含 WP-CLI 命令，也可以仅以某种方式扩展 WP-CLI。

要查找可安装的现有包，请查看 [Packagist](https://packagist.org/?type=wp-cli-package)。

## 安装包

使用 `wp package install` 命令安装包。包可以指定为：

* WP-CLI 包索引中的包名称
* 当前 shell 用户可访问的 Git URL
* 本地机器上的目录路径
* 本地或远程的 .zip 文件

```bash
# 按名称安装包
wp package install wp-cli/server-command

# 从 Git URL 安装
wp package install https://github.com/wp-cli/server-command.git

# 从本地目录安装
wp package install /path/to/package

# 从 .zip 文件安装
wp package install package.zip
```

默认情况下，包安装到 `~/.wp-cli/packages/`。使用 `WP_CLI_PACKAGES_DIR` 环境变量提供自定义路径。另请参阅：[共享 WP-CLI 包](https://make.wordpress.org/cli/handbook/guides/sharing-wp-cli-packages/)。

## 版本约束

安装 WP-CLI 包时，可以指定版本约束来控制安装包的哪个版本。

版本约束通过在包名称后追加冒号（`:`）和约束来指定：

```bash
wp package install <package-name>:<version-constraint>
```

WP-CLI 使用 Composer 的版本约束语法。以下是一些常用示例：

```bash
# 安装特定版本
wp package install wp-cli/server-command:2.0.0

# 使用脱字符操作符安装（允许非破坏性更新）
wp package install wp-cli/server-command:^1.0

# 使用波浪号操作符安装（允许补丁级别更新）
wp package install wp-cli/server-command:~1.2

# 安装最新的稳定版本
wp package install wp-cli/server-command:@stable

# 从开发分支安装
wp package install wp-cli/server-command:dev-main
```

有关版本约束语法和操作符的完整文档，请参阅 [Composer 关于版本和约束的文档](https://getcomposer.org/doc/articles/versions.md)。