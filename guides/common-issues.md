---
title: "常见问题"
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

# 常见问题

### 错误：无法连接到数据库

可能的原因：

a) 您正在使用 MAMP，但 WP-CLI 未使用 MAMP 的 PHP 二进制文件。

您可以通过运行 `wp --info` 来检查 WP-CLI 正在使用哪个 PHP。

如果需要指定其他 PHP 二进制文件，请参阅[使用自定义 PHP 二进制文件](https://make.wordpress.org/cli/handbook/installing/#using-a-custom-php-binary)。

b) 这是一个 WordPress 多站点安装。

c) `wp-config.php` 中的数据库凭据实际上不正确。

### 运行 `wp --info` 产生 HTML 输出

如果在禁用 Phar 支持的服务器上运行 `wp --info`，你可能会看到：

```
$ wp --info
Content-type: text/html; charset=UTF-8
```

使用 WP-CLI Phar 时，你需要在 `php.ini` 中将 Phar 支持加入白名单：

```
suhosin.executor.include.whitelist = phar
```

### PHP 致命错误：无法重新声明 wp_unregister_GLOBALS()

如果在运行 `wp` 命令时遇到此致命错误，可能是因为您移动或编辑了 `wp-config.php` 文件，超出了 wp-cli 支持的范围：

```
PHP Fatal error: Cannot redeclare wp_unregister_GLOBALS() (previously declared in /var/www/foo.com/wp-includes/load.php:18) in /var/www/foo.com/wp-includes/load.php on line 33
```

WP-CLI 的一个要求是，以下代码行：

```php
require_once(ABSPATH . 'wp-settings.php');
```

必须保留在 `wp-config.php` 文件中。因此，如果您修改或移动了它，请将其放回原处。当 WP-CLI 运行时，会通过正则表达式匹配此行。

### PHP Fatal error: Call to undefined function `<WordPress function>`

Before WP-CLI can load `wp-settings.php`, it needs to know all of the constants defined in `wp-config.php` (database connection details and so on). Because WP-CLI doesn't want WordPress to load yet when it's [pulling the constants](https://github.com/wp-cli/wp-cli/blob/main/php/wp-cli.php#L22) out of `wp-config.php`, [it uses regex](https://github.com/wp-cli/wp-cli/blob/main/php/WP_CLI/Runner.php#L324) to strip the `require_once(ABSPATH . 'wp-settings.php');` statement.

If you've modified your `wp-config.php` in a way that calls WordPress functions, PHP will fail out with a fatal error, as your `wp-config.php` is calling a WordPress function before WordPress has been loaded to define it.

Example:

```Shell
$ wp core check-update
PHP Fatal error:  Call to undefined function add_filter() in phar:///usr/local/bin/wp/php/WP_CLI/Runner.php(952) : eval()'d code on line N
```

Modifying `wp-config.php` beyond constant definitions is not best practice. You should move any modifications to a [WordPress mu-plugin](https://developer.wordpress.org/advanced-administration/plugins/mu-plugins/), which will retain the functionality of your modifications while allowing wp-cli to parse your wp-config.php without throwing a PHP error, as well as preventing other errors.

See: [#1631](https://github.com/wp-cli/wp-cli/issues/1631)

### PHP 致命错误：调用未定义函数 cli\posix_isatty()

请确保已安装 php-process 扩展。例如在 Centos 6 上：`yum install php-process`

### PHP 致命错误：允许的内存大小 999999 字节已耗尽（尝试分配 99 字节）

如果在运行 `wp package install` 时遇到与内存相关的 PHP 致命错误，很可能是内存不足。

WP-CLI 底层使用 Composer 来管理 WP-CLI 包。然而，Composer 比较消耗内存，因此需要增加内存限制以适应它。

编辑 `php.ini` 作为永久解决方案：

```bash
# 查找 PHP-CLI 的 php.ini
$ php -i | grep php.ini
Configuration File (php.ini) Path => /usr/local/etc/php/7.0
Loaded Configuration File => /usr/local/etc/php/7.0/php.ini
# 将 memory_limit 增加到 512M 或更高
$ vim /usr/local/etc/php/7.0/php.ini
memory_limit = 512M
```

临时设置 `memory_limit` 作为快速修复：

```bash
$ php -d memory_limit=512M "$(which wp)" package install <package-name>
```

如果 PHP 进程仍然内存不足，请尝试以下步骤：

1. 重启 PHP。
2. 检查额外的 php.ini 文件：

```bash
$ php -i | grep additional
Scan this dir for additional .ini files => /usr/local/etc/php/7.1/conf.d
# 编辑额外的文件并将 memory_limit 增加到 512M 或更高
$ vim /usr/local/etc/php/7.1/conf.d
memory_limit = 512M
```

### 错误：糟糕！检测到您正在以 root 身份运行此命令。

以 root 身份运行 WP-CLI 极其危险。当您以 root 身份执行 WP-CLI 时，WordPress 实例内的任何代码（包括您安装的第三方插件和主题）都将拥有对整个服务器的完全权限。这可能导致 WordPress 实例中的恶意代码危害整个服务器。

WP-CLI 项目强烈反对以 root 身份运行 WP-CLI。

另请参阅：[#973](https://github.com/wp-cli/wp-cli/pull/973#issuecomment-35842969)

### PHP 提示：`$_SERVER` 超全局变量中的未定义索引

`$_SERVER` 超全局变量是一个通常由 Web 服务器填充的数组，包含诸如头部信息、路径和脚本位置等信息。PHP CLI 不会填充此变量，WP-CLI 也不会，因为许多变量细节在命令行环境下没有意义。

在访问 `$_SERVER` 超全局变量中的值之前，你应该检查键是否已设置：

    if ( isset( $_SERVER['HTTP_X_FORWARDED_PROTO'] ) && 'https' === $_SERVER['HTTP_X_FORWARDED_PROTO'] ) {
      $_SERVER['HTTPS']='on';
    }

当在 `wp-config.php` 中使用 `$_SERVER['HTTP_HOST']` 时，你需要在 WP-CLI 上下文中设置一个默认值：

    if ( defined( 'WP_CLI' ) && WP_CLI && ! isset( $_SERVER['HTTP_HOST'] ) ) {
        $_SERVER['HTTP_HOST'] = 'example.com';
    }

另请参阅：[#730](https://github.com/wp-cli/wp-cli/issues/730)

### PHP 提示：使用了未定义的常量 STDOUT

`STDOUT` 常量由 PHP CLI 定义。如果您收到 `STDOUT` 缺失的错误提示，很可能是因为您没有通过 PHP CLI 运行 WP-CLI。请相应地检查您的服务器配置。

### PHP 解析错误：语法错误，在 .../php/WP_CLI/Runner.php ... eval()'d 代码的第 1 行出现意外的 '?'

如果在运行 `wp` 命令时遇到此错误，最可能的原因是您的 `wp-config.php` 文件开头存在 [Unicode `BOM`](https://en.wikipedia.org/wiki/Byte_order_mark)。此问题将在未来的 WP-CLI 版本中解决，但在此期间，您可以通过运行以下命令来解决：

    $ sed -i '1s/^\xEF\xBB\xBF//' $(wp config path)

或者使用您喜欢的编辑器手动移除 `BOM`。

另请参阅：[wp-cli/search-replace-command#71](https://github.com/wp-cli/search-replace-command/issues/71)

### 无法找到 wp-content 目录 / `$_SERVER['document_root']` 的使用问题

`$_SERVER['document_root']` 由网络服务器根据传入的 Web 请求定义。由于 PHP CLI 无法获取此类上下文，因此 WP-CLI 也无法使用 `$_SERVER['document_root']`。此外，WP-CLI 无法像处理 `$_SERVER['http_host']` 和其他一些 `$_SERVER` 值那样安全地模拟 `$_SERVER['document_root']`。

如果您在 `wp-config.php` 文件中使用了 `$_SERVER['document_root']`，应改用 `dirname( __FILE__ )` 或类似方法。

另请参阅：[#785](https://github.com/wp-cli/wp-cli/issues/785)

### 全局参数与命令参数冲突

所有[全局参数](https://make.wordpress.org/cli/handbook/references/config/#global-parameters)（例如 `--url=<url>`）都可能与你希望为命令接受的参数发生冲突。例如，向侧边栏添加 RSS 小工具时，可能无法正确设置该小工具的订阅源 URL：

    $ wp widget add rss sidebar-1 1 --url="http://www.smashingmagazine.com/feed/" --items=3
    Success: Added widget to sidebar.

* 预期结果：小工具已设置订阅源 URL。
* 实际结果：小工具已添加且项目数量设置为 3，但订阅源 URL 为空。

使用 `WP_CLI_STRICT_ARGS_MODE` 环境变量来告知 WP-CLI 将命令前的所有参数视为全局参数，命令后的参数视为本地参数：

    WP_CLI_STRICT_ARGS_MODE=1 wp --url=wp.dev/site2 widget add rss sidebar-1 1 --url="http://wp-cli.org/feed/"

在此示例中，`--url=wp.dev/site2` 是全局参数，用于设置 WP-CLI 在 WordPress 多站点安装中针对 'site2' 运行。`--url="http://wp-cli.org/feed/"` 是本地参数，用于为 RSS 订阅源小工具设置正确的 URL。

另请参阅：[#3128](https://github.com/wp-cli/wp-cli/pull/3128)

### 警告：有代码尝试进行 URL 重定向

多数情况下，这是某些插件或主题代码禁用了非管理员对 wp-admin 的访问。

除了禁用保护功能外，一个快速解决方法是传递用户参数：`--user=some_admin`

另请参阅：[#477](https://github.com/wp-cli/wp-cli/issues/477)

### Cannot create a post with Latin characters in the title on Windows

Considering the following example:

    wp post create --post_title="Perícias Contábeis"

Using UTF-8 in PHP arguments doesn't work on Windows for PHP <= 7.0, however it will work for PHP >= 7.1, as it was fixed as part of [Support for long and UTF-8 path](http://php.net/manual/en/migration71.windows-support.php). A workaround for PHP <= 7.0 is to use the `--prompt` option:

    echo "Perícias Contábeis" | wp post create --post_type=page --post_status=publish --prompt=post_title

See also: [#4714](https://github.com/wp-cli/wp-cli/issues/4714)

### 安装过程卡住

如果在尝试从 GitHub 克隆资源时，安装过程似乎一直卡住，请确保您的网络允许通过 SSL（端口 443）和 Git（端口 9418）建立出站连接来访问 GitHub。

### W3 Total Cache 错误：部分文件似乎缺失或位置不正确。

W3 Total Cache 的对象缓存功能可能导致此问题。禁用对象缓存并可选地删除 `wp-content/object-cache.php` 文件将使 WP-CLI 恢复正常工作。

另请参阅：[#587](https://github.com/wp-cli/wp-cli/issues/587)

### 自动更新程序不适用于 3.4 之前的版本

`wp core update` 命令设计用于 WordPress 3.4 及以上版本。要将旧版网站更新到最新的 WordPress，您可以尝试以下替代方案之一：

1.  **全自动方式：** 运行 `wp core download --force` 下载最新的 WordPress 并替换您的文件（别担心，`wp-config.php` 文件将保持不变）。然后，运行 `wp core update-db` 来更新数据库。由于此过程并非完美，请再次运行 `wp core download --force`，新版本应该就绪了。
2.  **半自动方式：** 运行 `wp core download --force` 下载所有文件并替换当前安装中的文件，然后访问 `/wp-admin/` 并在提示时运行数据库升级。

### PHP 致命错误：函数嵌套层级已达 '#' 的最大限制，正在中止！

您遇到了与 [PHP Xdebug](https://xdebug.org/) 相关的限制。以下是几种解决方案：

1.  执行 CLI 命令时临时关闭 Xdebug：`XDEBUG_MODE=off wp <command> ...`
2.  在您的 `php.ini` 文件中增加 `xdebug.max_nesting_level` 的值。您可以在此处了解更多信息 - [`xdebug.max-nesting-level`](https://xdebug.org/docs/all_settings#max_nesting_level)

如果您希望在保留调试工具的同时快速解决问题，可以更改 `max_nesting_level` 值来执行一次命令：

`php -d xdebug.max_nesting_level=512 wp <command> ...`

如果您当前不在调试代码，建议完全禁用 Xdebug。有关如何永久关闭 Xdebug 的说明，请参考您的本地环境或托管服务提供商的文档。

您可能会遇到类似问题，但错误信息不同：`错误：Xdebug 检测到可能的无限循环，并已中止您的脚本，堆栈深度为 '#' 帧`