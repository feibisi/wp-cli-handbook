---
title: "Implementation Details"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Contributions
    - Repos
    - Data
---

# Implementation Details

This page contains some history on various implementation details of WP-CLI.

## Bootstrapping WordPress

On a normal web request, your web server calls the `index.php` file in the root of the web directory to bootstrap the WordPress load process:

```
<?php
/**
 * Front to the WordPress application. This file doesn't do anything, but loads
 * wp-blog-header.php which does and tells WordPress to load the theme.
 *
 * @package WordPress
 */

/**
 * Tells WordPress to load the WordPress theme and output it.
 *
 * @var bool
 */
define('WP_USE_THEMES', true);

/** Loads the WordPress Environment and Template */
require( dirname( __FILE__ ) . '/wp-blog-header.php' );
```

You'll notice `index.php` calls `wp-blog-header.php`, which then calls `wp-load.php`, which then calls `wp-config.php`, which then calls `wp-settings.php`.

This last file, `wp-settings.php`, is WordPress' primary bootstrap file. It loads your plugins, active theme, and calls the `init` action.

On the command line, WP-CLI follows a similar process to bootstrap WordPress. However, instead of loading `index.php`, using the `wp` command starts with this:

```
<?php

// Can be used by plugins/themes to check if WP-CLI is running or not
define( 'WP_CLI', true );
define( 'WP_CLI_VERSION', trim( file_get_contents( WP_CLI_ROOT . '/VERSION' ) ) );
define( 'WP_CLI_START_MICROTIME', microtime( true ) );

// Set common headers, to prevent warnings from plugins
$_SERVER['SERVER_PROTOCOL'] = 'HTTP/1.0';
$_SERVER['HTTP_USER_AGENT'] = '';
$_SERVER['REQUEST_METHOD'] = 'GET';
$_SERVER['REMOTE_ADDR'] = '127.0.0.1';

include WP_CLI_ROOT . '/php/utils.php';
include WP_CLI_ROOT . '/php/dispatcher.php';
include WP_CLI_ROOT . '/php/class-wp-cli.php';
include WP_CLI_ROOT . '/php/class-wp-cli-command.php';

\WP_CLI\Utils\load_dependencies();

WP_CLI::get_runner()->start();
```

WP-CLI includes a good amount of setup code prior to calling `wp-settings.php`. Its bootstrapping process is different than a web request in a couple of notable ways.

### `wp-config.php` 文件会被解析并执行

WP-CLI 并非直接调用 `wp-config.php`，而是获取其内容，解析出 `require_once ABSPATH . 'wp-settings.php';` 语句，并通过 `eval()` 将常量加载到作用域中。阅读《[WP-CLI 如何加载 WordPress](https://make.wordpress.org/cli/2013/10/24/how-wp-cli-loads-wordpress/)》了解历史原因。此后，WP-CLI 在 v0.24.0 版本前使用自定义的 `wp-settings-cli.php` [[#2278](https://github.com/wp-cli/wp-cli/issues/2278)]，但为保持向后兼容性，仍保留解析 `wp-config.php` 的方式。另见 [#1631](https://github.com/wp-cli/wp-cli/issues/1631)。

### WordPress 在函数内部加载

WP-CLI 通过 `WP_CLI::get_runner()->load_wordpress()` 方法加载 WordPress，这意味着 WordPress 插件和主题不会在全局作用域中加载。插件或主题中使用的任何全局变量都需要显式声明为全局变量。关于此决策的历史背景，请参阅 [#2089](https://github.com/wp-cli/wp-cli/issues/2089)。

当 `WP_CLI::get_runner()->load_wordpress()` 调用 `wp-settings.php` 后，WordPress 会处理剩余的引导流程。

## 命令帮助文本

`wp help <command>` 功能经历了多次演变。

自 WP-CLI 0.3 起，如果命令类中存在静态 `help()` 方法，则会调用该方法。([48a8887d](https://github.com/wp-cli/wp-cli/commit/48a8887d46be25e0c0ad326975729ec816c17331))

自 WP-CLI 0.6 起，系统会查找 `<command>.1` ROFF 文件并使用 `man` 命令显示。该 ROFF 文件由对应的 `<command>.txt` Markdown 文件和 PHPDoc 元数据编译生成。([#24](https://github.com/wp-cli/wp-cli/issues/24))

自 WP-CLI 0.11 起，帮助文本改为实时动态生成。([#548](https://github.com/wp-cli/wp-cli/pull/548))

## WP_ADMIN

大多数 WP-CLI 命令执行管理操作，需要访问 `wp-admin/includes` 中定义的代码。这些代码可以按需加载或预先加载。

问题在于：`WP_ADMIN` 常量应该设置为 `true` 还是 `false`？

最初，WP-CLI 只是加载 wp-admin 代码，完全不处理 WP_ADMIN 常量。

后来，为了进行集成测试（[#69](https://github.com/wp-cli/wp-cli/issues/69)），它假装执行前端页面加载。<sup><a href="#note-1">[1]</a></sup>

接着它又假装正在加载 wp-admin，以绕过缓存插件（[#164](https://github.com/wp-cli/wp-cli/issues/164)）。

然后它不再假装加载 wp-admin（[#352](https://github.com/wp-cli/wp-cli/issues/352)），因为我们找到了更好的方法来绕过缓存插件。<sup><a href="#note-2">[2]</a></sup>

----

* <sup><a name="note-1">[1]</a></sup>: 事实证明，官方 WordPress 测试套件有更好的解决方案：`go_to()` 方法。
* <sup><a name="note-2">[2]</a></sup>: 解决方案是我们自己编写 `wp-settings.php` 文件。