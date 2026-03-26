---
title: "wp scaffold plugin"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Scaffold
    - Commands
    - Repos
---

# wp scaffold plugin

生成插件的基础代码。

始终会生成以下文件：

* `plugin-slug.php` 是主要的 PHP 插件文件。
* `readme.txt` 是插件的说明文件。
* `package.json` 是 NPM 所需的文件，包含项目相关的各种元数据。包含的包：`grunt`、`grunt-wp-i18n` 和 `grunt-wp-readme-to-markdown`。脚本：`start`、`readme`、`i18n`。
* `Gruntfile.js` 是包含 Grunt 任务的 JS 文件。任务：`i18n`（包含 `addtextdomain` 和 `makepot`），`readme`（包含 `wp_readme_to_markdown`）。
* `.editorconfig` 是 Editor 的配置文件。
* `.gitignore` 告诉 git 应该忽略哪些文件（或模式）。
* `.distignore` 告诉在分发时应忽略哪些文件和文件夹。

除非使用 `--skip-tests` 参数，否则还会包含以下文件：

* `phpunit.xml.dist` 是 PHPUnit 的配置文件。
* `.circleci/config.yml` 是 CircleCI 的配置文件。使用 `--ci=<provider>` 来选择不同的服务。
* `bin/install-wp-tests.sh` 配置 WordPress 测试套件和测试数据库。
* `tests/bootstrap.php` 是在运行测试套件时激活当前插件的文件。
* `tests/test-sample.php` 是包含测试用例的示例文件。
* `.phpcs.xml.dist` 是 PHP_CodeSniffer 规则的集合。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

&lt;slug&gt;
: 插件的内部名称。

[\--dir=&lt;dirname&gt;]
: 将新插件放在任意目录路径中。插件目录将是路径加上提供的 slug。

[\--plugin_name=&lt;title&gt;]
: 在 'Plugin Name:' 头部中填写的内容。

[\--plugin_description=&lt;description&gt;]
: 在 'Description:' 头部中填写的内容。

[\--plugin_author=&lt;author&gt;]
: 在 'Author:' 头部中填写的内容。

[\--plugin_author_uri=&lt;url&gt;]
: 在 'Author URI:' 头部中填写的内容。

[\--plugin_uri=&lt;url&gt;]
: 在 'Plugin URI:' 头部中填写的内容。

[\--skip-tests]
: 不生成用于单元测试的文件。

[\--ci=&lt;provider&gt;]
: 为持续集成提供商选择配置文件。
\---
默认值: circle
选项:
  - circle
  - gitlab
  - bitbucket
  - github
\---

[\--activate]
: 激活新生成的插件。

[\--activate-network]
: 在网络中激活新生成的插件。

[\--force]
: 覆盖已存在的文件。

### EXAMPLES

    $ wp scaffold plugin sample-plugin
    Success: Created plugin files.
    Success: Created test files.

### GLOBAL PARAMETERS

These [global parameters](https://make.wordpress.org/cli/handbook/config/) have the same behavior across all commands and affect how WP-CLI interacts with WordPress.

| **Argument**    | **Description**              |
|:----------------|:-----------------------------|
| `--path=<path>` | Path to the WordPress files. |
| `--url=<url>` | Pretend request came from given URL. In multisite, this argument is how the target site is specified. |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | Perform operation against a remote server over SSH (or a container using scheme of "docker", "docker-compose", "docker-compose-run", "vagrant"). |
| `--http=<http>` | Perform operation against a remote WordPress installation over HTTP. |
| `--user=<id\|login\|email>` | Set the WordPress user. |
| `--skip-plugins[=<plugins>]` | Skip loading all plugins, or a comma-separated list of plugins. Note: mu-plugins are still loaded. |
| `--skip-themes[=<themes>]` | Skip loading all themes, or a comma-separated list of themes. |
| `--skip-packages` | Skip loading all installed packages. |
| `--require=<path>` | Load PHP file before running the command (may be used more than once). |
| `--exec=<php-code>` | Execute PHP code before running the command (may be used more than once). |
| `--context=<context>` | Load WordPress in a given context. |
| `--[no-]color` | Whether to colorize the output. |
| `--debug[=<group>]` | Show all PHP errors and add verbosity to WP-CLI output. Built-in groups include: bootstrap, commandfactory, and help. |
| `--prompt[=<assoc>]` | Prompt the user to enter values for all command arguments, or a subset specified as comma-separated values. |
| `--quiet` | Suppress informational messages. |