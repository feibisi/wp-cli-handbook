---
title: "插件集成测试"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - How To
    - Repos
    - Data
---

# 插件集成测试

本指南演示如何在 Travis CI 和本地运行集成测试。脚手架使用 WordPress 核心的"单元测试"来对 WordPress 核心进行单元测试。单元测试同样适用于测试插件和主题，但若以此方式使用，这些测试将转变为"集成测试"——它们测试插件/主题与 WordPress 核心之间的集成。针对插件或主题的适当单元测试不应加载 WordPress。

## 在 Travis CI 上运行测试

如果您将插件托管在 GitHub 上并启用 [Travis CI](https://docs.travis-ci.com/)，那么每次提交到插件后，测试都会自动运行。

要启用此功能，您只需从 [WP-CLI 示例插件](https://github.com/wp-cli/sample-plugin) 复制并编辑以下文件：

* `.travis.yml`、`phpunit.xml.dist` 和 `phpcs.ruleset.xml` 文件
* `tests` 文件夹

请参阅文档以了解 [每个文件的作用说明](https://developer.wordpress.org/cli/commands/scaffold/plugin-tests/)。然后，您需要在 `tests/` 文件夹中指定您的单元测试。

## 本地运行测试

在开发过程中本地运行测试是有益的，因为这比提交更改并等待 Travis CI 运行测试更快。

我们假设：

* 您已有一个名为 `my-plugin` 的插件
* 您已安装 `git`、`svn`、`php`、`apache`（[如何在 Ubuntu 16.04 上安装 LAMP 堆栈](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04)）

那么，让我们开始吧：

### 1. [安装 PHPUnit](https://github.com/sebastianbergmann/phpunit#installation)

需要安装的 PHPUnit 版本取决于 PHP 和 WordPress 的版本。
请参阅：[PHPUnit 兼容性与 WordPress 版本 – Make WordPress Core](https://make.wordpress.org/core/handbook/references/phpunit-compatibility-and-wordpress-versions/)

### 2. 生成插件测试文件

  ```bash
  wp scaffold plugin-tests my-plugin
  ```

此命令将生成运行测试所需的所有文件，包括一个 `.travis.yml` 文件。

### 3. 在本地初始化测试环境

`cd` 进入插件目录并运行安装脚本（你需要已安装 `wget`）。

  ```bash
  bash bin/install-wp-tests.sh wordpress_test root '' localhost latest
  ```

安装脚本首先会在 `/tmp` 目录（默认）中安装一份 WordPress 副本以及 WordPress 单元测试工具。然后它会创建一个用于运行测试的数据库。传递给 `install-wp-tests.sh` 的参数用于设置测试数据库。

* `wordpress_test` 是测试数据库的名称（**所有数据将被删除！**）
* `root` 是 MySQL 用户名
* `''` 是 MySQL 用户密码
* `localhost` 是 MySQL 服务器主机
* `latest` 是 WordPress 版本；也可以是 `3.7`、`3.6.2` 等。

注意：此脚本可以多次运行而不会出错，但它*不会*覆盖先前已存在的文件。因此，如果你的数据库凭据更改，或者你想切换到不同的 MySQL 实例，仅重新运行脚本是不够的。你需要手动编辑安装在 `/tmp` 目录中的 `wp-config.php` 文件。

### 4. 运行插件测试

```bash
phpunit
```

如果在运行安装脚本或 PHPUnit 时遇到问题，请查看[支持部分](http://wp-cli.org/#support)以获取帮助和常见问题的解答。

## 在 Windows 中集成 WP 单元测试

尝试在 Windows 中为您的项目设置单元测试时遇到困难了吗？

首先，要知道一些 WP-CLI 命令在 Windows 中无法工作，因此您需要使用 Cygwin。Cygwin 也是[WordPress 核心项目推荐的工具](https://make.wordpress.org/core/handbook/tutorials/working-with-patches/)。

其次，`bin/install-wp-tests.sh` 脚本无法直接在 Windows 中运行。Windows 10 [引入了 Windows Subsystem for Linux](http://www.pcworld.com/article/3106463/windows/how-to-get-bash-on-windows-10-with-the-anniversary-update.html)，但旧版本需要额外努力。推荐使用 Cygwin，因为它默认运行 bash 脚本。

第三，bash 安装脚本使用了 `which` 命令，这是一个在 Windows 中默认不可用的 Linux 命令。`cURL`、`svn` 和 `wget` 都可以在 Windows 中作为单独的软件包安装。

最后，有时 bash 脚本会因为使用临时文件夹的方式而无法构建 WordPress。如果失败，您可以手动将 WordPress 安装到可写目录，然后手动创建 `wp-tests-config.php`。