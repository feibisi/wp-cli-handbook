---
title: "wp scaffold theme-tests"
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

# wp scaffold theme-tests

生成在主题中运行 PHPUnit 测试所需的文件。

默认生成以下文件：

* `phpunit.xml.dist` 是 PHPUnit 的配置文件。
* `.circleci/config.yml` 是 CircleCI 的配置文件。使用 `--ci=<provider>` 选择其他服务。
* `bin/install-wp-tests.sh` 配置 WordPress 测试套件和测试数据库。
* `tests/bootstrap.php` 是在运行测试套件时激活当前主题的文件。
* `tests/test-sample.php` 是包含实际测试的示例文件。
* `.phpcs.xml.dist` 是 PHP_CodeSniffer 规则的集合。

从[插件单元测试文档](https://make.wordpress.org/cli/handbook/misc/plugin-unit-tests/)了解更多信息。

### 环境配置

`tests/bootstrap.php` 文件会查找 WP_TESTS_DIR 环境变量。

### 选项说明

关于所用语法约定的详细解释，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考文档。

[&lt;theme&gt;]
: 要为其生成测试文件的主题名称。

[\--dir=&lt;dirname&gt;]
: 为非标准主题路径生成测试文件。如果未指定主题别名，则使用目录名。

[\--ci=&lt;provider&gt;]
: 为持续集成服务商选择配置文件。
\---
默认值: circle
可选值:
  - circle
  - gitlab
  - bitbucket
  - github
\---

[\--force]
: 覆盖已存在的文件。

### EXAMPLES

    # Generate unit test files for theme 'twentysixteenchild'.
    $ wp scaffold theme-tests twentysixteenchild
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