---
title: "快速开始"
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

# 快速开始

恭喜！您已[安装 WP-CLI](https://make.wordpress.org/cli/handbook/installing/)，准备提升 WordPress 使用技能。本页简要介绍 WP-CLI 并附使用示例。

## 简介

WP-CLI 是 WordPress 的命令行界面。该项目的目标是提供一个完全替代 WordPress 管理后台的方案；对于任何你可能想在 WordPress 管理后台执行的操作，都应该有一个等效的 WP-CLI 命令。

例如，既然你可以从 WordPress 管理后台安装插件，你也可以通过 WP-CLI [安装插件](https://developer.wordpress.org/cli/commands/plugin/install/)：

    $ wp plugin install akismet
    Installing Akismet (3.1.8)
    Downloading install package from https://downloads.wordpress.org/plugin/akismet.3.1.8.zip...
    Unpacking the package...
    Installing the plugin...
    Plugin installed successfully.

同样，既然你也可以从 WordPress 管理后台激活插件，你也可以通过 WP-CLI [激活插件](https://developer.wordpress.org/cli/commands/plugin/activate/)：

    $ wp plugin activate akismet
    Success: Plugin 'akismet' activated.

使用 WordPress 管理后台和 WP-CLI 的一个关键区别是：执行任何操作所需的点击次数都少得多。随着你对命令行越来越熟悉，你会发现使用 WP-CLI 执行特定任务通常比通过 WordPress 管理后台执行相同任务要快得多。前期投入时间学习如何更好地使用 WP-CLI，从长远来看会带来回报。

## 常用术语

在使用 WP-CLI 的过程中，你会反复听到某些术语。

例如，_命令_ 是 WP-CLI 功能的最小单元。`wp plugin install` 是一个命令，`wp plugin activate` 也是。命令包含名称（如 'plugin install'）和回调函数，并通过 `WP_CLI::add_command()` 注册（[文档](https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-command/)）。

_概要_ 定义了命令接受的_位置_参数和_关联_参数。我们来看看 `wp plugin install` 的概要：

    $ wp plugin install
    usage: wp plugin install <plugin|zip|url>... [--version=<version>] [--force] [--activate] [--activate-network]

在这个例子中，`<plugin|zip|url>...` 是接受的_位置_参数。实际上，`wp plugin install` 可以多次接受相同的位置参数（要安装的插件别名、ZIP 文件或 URL）。`[--version=<version>]` 是接受的_关联_参数之一，用于指定要安装的插件版本。同时注意参数定义周围的方括号；方括号表示该参数是可选的。

WP-CLI 还有一系列适用于所有命令的[_全局_参数](https://make.wordpress.org/cli/handbook/config/)。例如，包含 `--debug` 意味着命令执行将显示所有 PHP 错误，并为 WP-CLI 启动过程增加额外详细信息。

## Practical Examples

Ready to dive in? Here are some common examples of how WP-CLI is used:

**Download and install WordPress in seconds**

1. Download the latest version of WordPress with `wp core download` ([doc](https://developer.wordpress.org/cli/commands/core/download/)).

```
$ wp core download --path=wpclidemo.dev
Creating directory '/srv/www/wpclidemo.dev/'.
Downloading WordPress 4.6.1 (en_US)...
Using cached file '/home/vagrant/.wp-cli/cache/core/wordpress-4.6.1-en_US.tar.gz'...
Success: WordPress downloaded.
```

2. Create a new wp-config.php file with `wp config create` ([doc](https://developer.wordpress.org/cli/commands/config/create/)).

```
$ cd wpclidemo.dev
$ wp config create --dbname=wpclidemo --dbuser=root --prompt=dbpass
1/10 [--dbpass=<dbpass>]:
Success: Generated 'wp-config.php' file.
```

3. Create the database based on wp-config.php with `wp db create` ([doc](https://developer.wordpress.org/cli/commands/db/create/)).

```
$ wp db create
Success: Database created.
```

4. Install WordPress with `wp core install` ([doc](https://developer.wordpress.org/cli/commands/core/install/)).

```
$ wp core install --url=wpclidemo.dev --title="WP-CLI" --admin_user=wpcli --admin_password=wpcli --admin_email=info@wp-cli.org
Success: WordPress installed successfully.
```

That's it!

**Update plugins to their latest version**

Use `wp plugin update --all` ([doc](https://developer.wordpress.org/cli/commands/plugin/update/)) to update all plugins to their latest version.

```
$ wp plugin update --all
Enabling Maintenance mode...
Downloading update from https://downloads.wordpress.org/plugin/akismet.3.1.11.zip...
Unpacking the update...
Installing the latest version...
Removing the old version of the plugin...
Plugin updated successfully.
Downloading update from https://downloads.wordpress.org/plugin/nginx-champuru.3.2.0.zip...
Unpacking the update...
Installing the latest version...
Removing the old version of the plugin...
Plugin updated successfully.
Disabling Maintenance mode...
Success: Updated 2/2 plugins.
+------------------------+-------------+-------------+---------+
| name                   | old_version | new_version | status  |
+------------------------+-------------+-------------+---------+
| akismet                | 3.1.3       | 3.1.11      | Updated |
| nginx-cache-controller | 3.1.1       | 3.2.0       | Updated |
+------------------------+-------------+-------------+---------+
```

**Add a user as a super-admin**

On multisite, use `wp super-admin add` ([doc](https://developer.wordpress.org/cli/commands/super-admin/add/)) to grant super admin capabilities to an existing user.

```
$ wp super-admin add wpcli
Success: Granted super-admin capabilities.
```

**Regenerate thumbnails**

If you've added or changed an image size registered with `add_image_size()`, you may want to use `wp media regenerate` ([doc](https://developer.wordpress.org/cli/commands/media/regenerate/)) so your theme displays the correct image size.

```
wp media regenerate --yes
Found 1 image to regenerate.
1/1 Regenerated thumbnails for "charlie-gpa" (ID 4).
Success: Finished regenerating the image.
```

**Search and replace URLs**

If you're moving a database from one domain to another, `wp search-replace` ([doc](https://developer.wordpress.org/cli/commands/search-replace/)) makes it easy to update all URL references in your database.

To see which links will be replaced in your database, use the --dry-run flag:

```
wp search-replace 'http://oldsite.com' 'http://newsite.com' --dry-run
```

When ready to replace the links, run:

```
wp search-replace 'http://oldsite.com' 'http://newsite.com'
```

Wondering what's next? Browse through [all of WP-CLI's commands](https://developer.wordpress.org/cli/commands/) to explore your new world. For more detailed information about creating custom commands, visit the [WP-CLI Commands Cookbook](https://make.wordpress.org/cli/handbook/guides/commands-cookbook/). Or, catch up with [shell friends](https://make.wordpress.org/cli/handbook/references/shell-friends/) to learn about helpful command line utilities.