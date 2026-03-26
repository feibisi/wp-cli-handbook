---
title: "wp dist-archive"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Commands
    - Repos
    - Data
---

# wp dist-archive

基于项目的 .distignore 文件创建分发归档。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

对于目录 'wp-content/plugins/hello-world' 中的插件，此命令会创建一个分发归档 'wp-content/plugins/hello-world.zip'。

您可以通过项目仓库中的 .distignore 文件指定要从归档中排除的文件或目录：

```
.distignore
.editorconfig
.git
.gitignore
.travis.yml
circle.yml
```

为多个项目使用一个分发归档命令，而不是在每个项目中编写 bash 脚本。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

&lt;path&gt;
: 包含 .distignore 文件的项目路径。

[&lt;target&gt;]
: 分发存档文件的路径和可选文件名。如果仅提供路径，则文件名默认为项目目录名加上可发现的版本号。此外，如果仅给出路径，则其指向的目录必须已存在，命令才能正常运行。

[\--create-target-dir]
: 根据需要自动创建目标目录。

[\--force]
: 如果存档文件已存在，则强制覆盖。

[\--plugin-dirname=&lt;plugin-slug&gt;]
: 设置存档解压目录的名称。默认为项目目录名。

[\--format=&lt;format&gt;]
: 选择存档的格式。
\---
默认值: zip
选项:
  - zip
  - targz
\---

[\--filename-format=&lt;filename-format&gt;]
: 为存档文件名使用自定义格式。可用的替换变量：{name}, {version}。如果提供了 &lt;target&gt; 参数或无法确定版本，则此选项将被忽略。
\---
默认值: "{name}.{version}"
\---

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