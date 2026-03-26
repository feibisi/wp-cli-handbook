---
title: "错误报告"
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

# 错误报告

认为自己发现了错误？我们很乐意帮助您解决它。

在创建新问题之前，您应该：

* [搜索现有问题](https://github.com/search?q=org%3Awp-cli+label%3Abug+is%3Aopen+sort%3Aupdated-desc&type=issues)，查看是否有现有的解决方案，或者是否已在较新版本中修复。
* 查阅我们关于[常见问题及其修复方法](https://make.wordpress.org/cli/handbook/common-issues/)的文档。值得通读页面上链接的 GitHub 问题，因为列出的错误可能不完全是你遇到的错误。
* 在全新的 WordPress 安装中重现该问题（例如，使用 Twenty Sixteen 或类似主题，且没有激活任何插件）。如果问题仅在自定义环境中重现，那么该问题是您环境中的错误，而不是 WP-CLI 的错误（确保启用 `WP_DEBUG`，这通常会让你更清楚地了解问题）。您或许能够[将错误追踪到特定的插件或主题](https://make.wordpress.org/cli/handbook/identify-plugin-theme-conflict/)。

在您进行了一些搜索并发现之前没有关于您错误的先例后，请在适当的仓库中创建一个新的 GitHub 问题。提供摘要、重现步骤、环境详情以及下面确定的其他具体信息，将有助于确保您提交一份完整的错误报告。

**摘要**

以叙述形式描述，例如“在测试功能 x 时，我遇到了 z。”

> **摘要：**
>
> 在 WP-CLI 的最新夜间版本上安装以下软件包后，我收到“不是已注册的 wp 命令错误”

**重现错误的步骤**

请尽可能详细和具体。最好回头再按照您的步骤操作一遍，以确保其他用户可以直接按照步骤重现问题，而无需假设任何操作。

> **重现步骤：**
>
> 1. 运行命令 'wp package install wp-cli/scaffold-package-command:@stable'
> 2. 允许安装过程完成
> 3. 显示 'Success: Package installed.'
> 4. 运行 'wp help scaffold package'
> 5. 观察到 'Error: 'scaffold package' is not a registered wp command.'

如果您有大量输出要分享，请[创建一个 GitHub gist](https://gist.github.com/) 并在问题中链接到它。

**环境**

您的错误也可能与环境相关。因为 WP-CLI 是一个在不同系统上行为不同的工具，如果您认为它们相关，请在您的问题中包含一些环境详情。

    # WP-CLI 在什么 PHP 环境中运行？
    wp cli info
    # 您是否运行了 suhosin？如果是，请确保已将 `suhosin.executor.include.whitelist = phar` 添加到您的 php.ini 中
    php -m | grep -i suhosin
    # 您可以分享 which wp 的结果吗？
    which -a wp
    stat $(which wp)
    # 您是否运行了任何软件包？如果某个软件包导致了问题，您可以使用 `--skip-packages` 来跳过加载它们
    wp package list

**结果和影响**

请解释该错误如何影响您的使用，包括严重程度（预期结果是什么，实际结果是什么？影响对象、方式和程度如何？）。

> **严重程度** - 高
> 
> **预期结果：** 运行 `wp help scaffold package` 显示已安装命令的帮助信息。
> 
> **实际结果：** 显示错误信息：'Error: 'scaffold package' is not a registered wp command'。
> 
> 此命令对我们业务的日常运作至关重要。其他 1.2k 用户也安装了此包，将受到影响。
> 
> 使用 WP-CLI `1.2.0-alpha-3182ac4` 版本时，已安装的包可以正常工作。

**变通方案**

是否存在任何变通方案？如果有，是什么？

> **变通方案：** 回退到可正常工作的 WP-CLI 版本

**相关诊断信息**

包含任何与问题相关的崩溃报告、堆栈跟踪或调试输出。问题的截图或 GIF 也很有帮助！

输出内容很多？可以通过[创建 GitHub gist](https://gist.github.com/) 并在问题中链接到它，使您的问题更容易理解。

如果在执行 WP-CLI 时包含 `--debug` 标志（例如 `wp post list --debug`），您可能会获得更详细的错误来源信息，以便包含在报告中。

> ```
> $ wp package install wp-cli/scaffold-package-command:@stable
> Installing package wp-cli/scaffold-package-command (@stable)
> Updating /root/.wp-cli/packages/composer.json to require the package...
> Using Composer to install the package...
> ---
> Loading composer repositories with package information
> Updating dependencies
> Resolving dependencies through SAT
> Dependency resolution completed in 0.001 seconds
> Analyzed 421 packages to resolve dependencies
> Analyzed 96 rules to resolve dependencies
> Package operations: 1 install, 0 updates, 0 removals
> Installs: wp-cli/scaffold-package-command:1.2.0
>  - Installing wp-cli/scaffold-package-command (1.2.0)
> Writing lock file
> Generating autoload files
> ---
> Success: Package installed.
> ```

>```
> $ wp help scaffold package --debug
> Debug (bootstrap): Loading packages from: /root/.wp-cli/packages/vendor/autoload.php (0.044s)
> Debug (bootstrap): No readable global config found (0.193s)
> Debug (bootstrap): No project config found (0.194s)
> Debug (bootstrap): argv: /usr/local/bin/wp help scaffold package --debug (0.194s)
> Debug (bootstrap): ABSPATH defined: /home/fu/public_html/ (0.195s)
> Debug (bootstrap): Begin WordPress load (0.195s)
> Debug (bootstrap): wp-config.php path: /home/fu/public_html/wp-config.php (0.196s)
> Debug (bootstrap): Loaded WordPress (1.323s)
> Debug (bootstrap): Running command: help (1.323s)
> Error: 'scaffold package' is not a registered wp command.
> ```

> wp scaffold package 命令同样无法工作：
> 
>```
> $ wp scaffold package
> Error: 'scaffold package' is not a registered subcommand of 'scaffold'. See 'wp help scaffold'.
> ```