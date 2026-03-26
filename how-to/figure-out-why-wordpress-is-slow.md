---
title: "找出 WordPress 运行缓慢的原因"
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

# 找出 WordPress 运行缓慢的原因

`wp profile` 是一个 WP-CLI 命令，可帮助您快速识别 WordPress 的慢速问题。它设计用于与 Xdebug 和 New Relic 协同工作，因为它易于部署到任何安装了 WP-CLI 的服务器上。通过 `wp profile`，您可以快速查看关键性能指标（执行时间、查询次数、缓存命中/未命中率等），以指导进一步的调试工作。

## 安装

首先，如果您尚未安装 `wp profile` 包，请先安装：

```
$ wp package install wp-cli/profile-command
```

### 步骤 1 - 分析 WordPress 加载过程

正在处理一个您以前从未接触过的缓慢 WordPress 安装？运行 `wp profile stage` 以查看 WordPress 加载过程每个阶段的指标。包含 `--url=<url>` 参数以模拟特定 URL 的请求。

```
$ wp profile stage --url=runcommand.io
+------------+---------+------------+-------------+-------------+------------+--------------+-----------+------------+--------------+---------------+
| stage      | time    | query_time | query_count | cache_ratio | cache_hits | cache_misses | hook_time | hook_count | request_time | request_count |
+------------+---------+------------+-------------+-------------+------------+--------------+-----------+------------+--------------+---------------+
| bootstrap  | 0.7597s | 0.0052s    | 14          | 93.21%      | 357        | 26           | 0.3328s   | 2717       | 0s           | 0             |
| main_query | 0.0131s | 0.0004s    | 3           | 94.29%      | 33         | 2            | 0.0065s   | 78         | 0s           | 0             |
| template   | 0.7041s | 0.0192s    | 147         | 92.16%      | 2350       | 200          | 0.6982s   | 6130       | 0s           | 0             |
+------------+---------+------------+-------------+-------------+------------+--------------+-----------+------------+--------------+---------------+
| total (3)  | 1.477s  | 0.0248s    | 164         | 93.22%      | 2740       | 228          | 1.0375s   | 8925       | 0s           | 0             |
+------------+---------+------------+-------------+-------------+------------+--------------+-----------+------------+--------------+---------------+
```

当 WordPress 处理来自浏览器的请求时，它本质上是在执行一个长的 PHP 脚本。`wp profile stage` 将该脚本分为三个阶段：

*   **bootstrap** 是 WordPress 进行自身设置、加载插件和主主题，并触发 `init` 钩子的阶段。
*   **main_query** 是 WordPress 将请求（例如 /2016/10/21/moms-birthday/）转换为主 WP_Query 的阶段。
*   **template** 是 WordPress 根据主查询确定要渲染哪个主题模板并进行渲染的阶段。

### 步骤 2 - 深入分析特定阶段

在上面的示例中，bootstrap 阶段似乎有点慢，让我们进一步深入分析。运行 `wp profile stage bootstrap` 命令可以进入指定阶段的高精度模式。使用 `--spotlight` 标志可以过滤掉接近零的结果。

```
$ wp profile stage bootstrap --url=runcommand.io --spotlight
+--------------------------+----------------+---------+------------+-------------+-------------+------------+--------------+--------------+---------------+
| hook                     | callback_count | time    | query_time | query_count | cache_ratio | cache_hits | cache_misses | request_time | request_count |
+--------------------------+----------------+---------+------------+-------------+-------------+------------+--------------+--------------+---------------+
| muplugins_loaded:before  |                | 0.1644s | 0.0017s    | 1           | 40%         | 2          | 3            | 0s           | 0             |
| muplugins_loaded         | 2              | 0.0005s | 0s         | 0           | 50%         | 1          | 1            | 0s           | 0             |
| plugins_loaded:before    |                | 0.1771s | 0.0008s    | 6           | 77.63%      | 59         | 17           | 0s           | 0             |
| plugins_loaded           | 14             | 0.0887s | 0s         | 0           | 100%        | 104        | 0            | 0s           | 0             |
| after_setup_theme:before |                | 0.043s  | 0s         | 0           | 100%        | 26         | 0            | 0s           | 0             |
| init                     | 82             | 0.1569s | 0.0018s    | 7           | 96.88%      | 155        | 5            | 0s           | 0             |
| wp_loaded:after          |                | 0.027s  | 0s         | 0           |             | 0          | 0            | 0s           | 0             |
+--------------------------+----------------+---------+------------+-------------+-------------+------------+--------------+--------------+---------------+
| total (7)                | 98             | 0.6575s | 0.0043s    | 14          | 77.42%      | 347        | 26           | 0s           | 0             |
+--------------------------+----------------+---------+------------+-------------+-------------+------------+--------------+--------------+---------------+
```

`wp profile` 会根据每个阶段的主要操作进一步细分。对于 bootstrap 阶段，主要操作包括 `muplugins_loaded`、`plugins_loaded` 和 `init`。你还可以看到一些中间操作，如 `plugins_loaded:before` 和 `wp_loaded:after`。这些中间操作对应于实际 WordPress 钩子之前（或之后）的脚本执行。在某种意义上，它们是伪钩子。

### 步骤 3 - 分析特定钩子

当您找到想要评估的特定钩子时，运行 `wp profile hook <hook>`。使用 `--fields=<fields>` 参数可将输出限制在特定字段。

```
$ wp profile hook plugins_loaded --url=runcommand.io --fields=callback,time,location
+------------------------------------------------------------+---------+-----------------------------------------------------------------+
| callback                                                   | time    | location                                                        |
+------------------------------------------------------------+---------+-----------------------------------------------------------------+
| wp_maybe_load_widgets()                                    | 0.0046s | wp-includes/functions.php:3501                                  |
| wp_maybe_load_embeds()                                     | 0.0003s | wp-includes/embed.php:162                                       |
| VaultPress_Hotfixes->protect_jetpack_402_from_oembed_xss() | 0s      | vaultpress/class.vaultpress-hotfixes.php:124                    |
| _wp_customize_include()                                    | 0s      | wp-includes/theme.php:2052                                      |
| EasyRecipePlus->pluginsLoaded()                            | 0.0013s | easyrecipeplus/lib/EasyRecipePlus.php:125                       |
| Gamajo\GenesisHeaderNav\genesis_header_nav_i18n()          | 0.0007s | genesis-header-nav/genesis-header-nav.php:61                    |
| DS_Public_Post_Preview::init()                             | 0.0001s | public-post-preview/public-post-preview.php:52                  |
| wpseo_load_textdomain()                                    | 0.0004s | wordpress-seo-premium/wp-seo-main.php:222                       |
| load_yoast_notifications()                                 | 0.0016s | wordpress-seo-premium/wp-seo-main.php:381                       |
| wpseo_init()                                               | 0.0329s | wordpress-seo-premium/wp-seo-main.php:240                       |
| wpseo_premium_init()                                       | 0.0019s | wordpress-seo-premium/wp-seo-premium.php:79                     |
| wpseo_frontend_init()                                      | 0.0007s | wordpress-seo-premium/wp-seo-main.php:274                       |
| Black_Studio_TinyMCE_Plugin->load_compatibility()          | 0.0016s | black-studio-tinymce-widget/black-studio-tinymce-widget.php:206 |
| Jetpack::load_modules()                                    | 0.0564s | jetpack/class.jetpack.php:1672                                  |
+------------------------------------------------------------+---------+-----------------------------------------------------------------+
| total (14)                                                 | 0.1026s |                                                                 |
+------------------------------------------------------------+---------+-----------------------------------------------------------------+
```

就是这样！我们发现 `wpseo_init()` 和 `Jetpack::load_modules()` 共同导致每个页面加载时间增加了约 100 毫秒。

借助 `wp profile`，找出 WordPress 变慢的原因变得轻而易举。