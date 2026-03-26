---
title: "故障排除指南"
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

# 故障排除指南

在 GitHub 仓库报告新问题前，请务必检查本地安装配置，某些设置通常会导致 WP-CLI 命令出现意外结果。

### 如何获取关于 WP-CLI 安装的详细信息？

WP-CLI 提供了 `wp --info` 命令，该命令会输出大量关于 WP-CLI 安装环境的信息。输出内容包括：
* 您使用的操作系统和 shell
* 运行 WP-CLI 所用的 PHP 二进制文件路径
* 使用的 PHP 版本
* WP-CLI 根目录的位置
* WP-CLI 的 vendor 目录位置
* 当前使用的 WP-CLI 二进制文件路径（phar 文件路径）
* WP-CLI 包的存储位置
* WP-CLI 全局和项目配置文件的路径
* 您使用的 WP-CLI 版本

### 开始调试问题前，我应该做什么？

在开始调试问题之前，请确保您使用的是最新版本的 WP-CLI。最新版本可能已经解决了您遇到的问题。命令 `wp cli update` 将升级您的 WP-CLI 版本或确认您已在使用最新版本。如果安装过程卡住，请确保您的网络允许通过 SSL（端口 443）和 git（端口 9418）进行出站连接到 GitHub。

### 如果 WP-CLI 输出与预期不符，我该怎么办？

在开始排查错误之前，您应该了解可能改变 WP-CLI 默认行为的因素，以及如何检查它们是否是问题的根源。修改此默认行为主要有五个子系统：环境变量、配置文件、WP-CLI 包、`wp-config.php` 文件和 WordPress 扩展（插件、主题、必须使用插件、放置式插件）。

#### 环境变量

工作环境的设置是运行 WP-CLI 的前提条件。您可以使用 shell 命令 `env` 来检查当前的环境设置。

如果您想通过 SSH 远程运行 WP-CLI，则要求远程服务器的路径中可访问 `wp` 命令。WP-CLI 的行为也可以通过环境变量在运行时进行更改：

* `WP_CLI_CACHE_DIR` - 存储 WP-CLI 文件缓存的目录。默认为 `~/.wp-cli/cache/`。
* `WP_CLI_CONFIG_PATH` - 全局 `config.yml` 文件的路径。默认为 `~/.wp-cli/config.yml`。
* `WP_CLI_CUSTOM_SHELL` - 允许用户覆盖默认使用的 `/bin/bash` shell。
* `WP_CLI_DISABLE_AUTO_CHECK_UPDATE` - 禁用 WP-CLI 的自动更新检查。
* `WP_CLI_DOCKER_NO_TTY` - 忽略检测到的 tty 状态，并在通过 ssh 对 docker 容器运行 WP-CLI 时从 `docker exec` 中移除 `--tty` 标志。
* `WP_CLI_DOCKER_NO_INTERACTIVE` - 忽略检测到的 tty 状态，并在通过 ssh 对 docker 容器运行 WP-CLI 时从 `docker exec` 中移除 `--interactive` 标志。
* `WP_CLI_PACKAGES_DIR` - 存储通过 WP-CLI 包管理器安装的包的目录。默认为 `~/.wp-cli/packages/`。
* `WP_CLI_PHP` - 覆盖系统默认值时使用的 PHP 二进制路径（仅适用于非 Phar 安装）。
* `WP_CLI_PHP_ARGS` - 调用 WP-CLI 时传递给 PHP 二进制文件的参数（仅适用于非 Phar 安装）。
* `WP_CLI_SSH_PRE_CMD` - 当使用 `--ssh=<ssh>` 时，在 WP-CLI 调用远程服务器上的 WP-CLI 之前执行一个命令。
* `WP_CLI_SSH_BINARY` - 当使用 `--ssh=<ssh>` 时，这是在远程机器上替代 `wp` 被调用的命令。
* `WP_CLI_STRICT_ARGS_MODE` - 通过告诉 WP-CLI 将命令前的任何参数视为全局参数，命令后的参数视为本地参数，来避免歧义。
* `WP_CLI_SUPPRESS_GLOBAL_PARAMS` - 设置为 `true` 以跳过在帮助屏幕末尾显示全局参数。这为高级用户节省了屏幕空间。
* `WP_CLI_FORCE_USER_LOGIN` - 设置为 `1` 以强制将提供给 `--user` 标志的值解释为登录名而非 ID，以解决类型歧义问题。
* `WP_CLI_EARLY_REQUIRE` - 在引导过程的早期加载一个或多个自定义 PHP 文件（逗号分隔）。
* `WP_CLI_REQUIRE` - 在引导过程之后加载一个或多个自定义 PHP 文件（逗号分隔）。这与命令行上的 `--require` 或 wp-cli.yml 配置文件中的 `require` 映射具有相同效果。
* `WP_CLI_USER_AGENT` - 设置某些插件和工具所依赖的 `$_SERVER['HTTP_USER_AGENT']` 值。

要按需设置环境变量，您可以将环境变量定义放在要运行的 WP-CLI 命令之前（例如 `EDITOR=vim wp post edit 1`）；要覆盖环境变量，请在您的 `~/.bashrc` 或 `~.zhsrc` 中使用 `export VARIABLE=value`。

#### WP-CLI 配置文件

配置文件允许您自定义 WP-CLI 的行为，以适应您个人或项目的需求。如果配置文件不正确或包含对默认行为的不必要修改，WP-CLI 的输出很可能会反映出错误。

请注意，项目配置文件可以覆盖全局配置文件中的设置。

重命名或删除您的配置文件并比较结果，以确定是否某个配置设置导致了问题。

#### WP-CLI 包

WP-CLI 包是基于 WP-CLI 构建的社区维护项目。它们可以包含 WP-CLI 命令，也可以仅以某种方式扩展 WP-CLI。虽然 WP-CLI 本身可能运行良好，但存在错误的包也可能导致意外结果。要跳过加载所有已安装的包，请使用 `wp --skip-packages`。

#### WordPress Configuration File (`wp-config.php`)

Errors may result from moving or editing `wp-config.php` beyond what WP-CLI supports. If you get a parse error, check the file encoding of your `wp-config.php` (UTF-8 without BOM).

Make sure that the line `require_once(ABSPATH . 'wp-settings.php');` remains in the `wp-config.php` file and don't modify `wp-config.php` beyond constant definitions. If you call WordPress functions within `wp-config.php`, PHP will fail with a fatal error.

If you want to use `$_SERVER['HTTP_HOST']` in your `wp-config.php`, you’ll need to set a default value in WP-CLI context:

```
if ( defined( 'WP_CLI' ) && WP_CLI && ! isset( $_SERVER['HTTP_HOST'] ) ) {
    $_SERVER['HTTP_HOST'] = `example.com';
}
```

Instead of `$_SERVER['document_root']` use `dirname( __FILE__ )` or similar.

#### WordPress 扩展

WordPress 主题和插件可能与 WP-CLI 的加载过程冲突，或通过重定向用户等方式产生干扰。它们通常基于在 WP-CLI 环境中不成立的假设，例如使用当前请求的主机名（这在命令行环境中是不存在的概念）。

您可以选择绕过特定插件和主题（例如 `--skip-plugins=akismet`），或完全跳过它们（`wp --skip-plugins --skip-themes`）。

### 如果 WP-CLI 报告错误，我该怎么办？

常见问题通常源于 `wp-config.php` 或 Web 服务器配置的更改。手册中的“[常见问题](https://make.wordpress.org/cli/handbook/common-issues/)”部分列出了最常见的错误信息，并解释了如何处理这些错误。

尝试在一个全新的 WordPress 安装环境中复现该问题，使用默认主题（Twenty …）且不安装任何插件。如果问题仅在自定义环境中出现，那么问题出在您的环境而非 WP-CLI。同时，请确保通过在你的 `wp-config.php` 中设置常量 `define( 'WP_DEBUG', true );` 来启用 WordPress 的调试模式。这可能会揭示您现有 WordPress 安装中的问题，而非由 WP-CLI 引起。

此外，您可以使用 WP-CLI 的全局参数 `--debug` 来显示所有 PHP 错误，并增加 WP-CLI 启动过程的详细输出。

### 我已检查以上所有内容，但仍有问题。在哪里可以报告问题？

如果您认为发现了错误，我们很乐意听取您的反馈以便修复。

WP-CLI 的错误报告在 GitHub 上处理。在创建新问题之前，请先[搜索现有问题](https://github.com/search?q=org%3Awp-cli+label%3Abug+is%3Aopen+sort%3Aupdated-desc&type=issues)，查看是否有现有的解决方案。如果您的错误没有已开放或已修复的问题，请[遵循我们提交错误报告的指南](https://make.wordpress.org/cli/handbook/bug-reports/)，以确保问题得到及时处理。提供以下概述、重现步骤、环境详情和其他具体信息将有助于确保您提交完整的错误报告。

请提供以下信息：
* 问题的概述（叙述形式），
* 详细且具体的重现步骤列表，
* 您工作环境的详细信息，
* 描述错误如何影响您的使用（即预期结果与实际结果的对比），包括严重程度，
* 可能的临时解决方案，以及
* 相关诊断信息，如崩溃报告、堆栈跟踪或调试输出。

您可以在[提交错误报告的指南](https://make.wordpress.org/cli/handbook/bug-reports/)中找到问题报告这些细节的详细说明。