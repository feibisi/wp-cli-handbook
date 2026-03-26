---
title: "参数语法"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - References
    - Repos
    - Data
---

# 参数语法

WP-CLI 命令使用标准化语法来描述其参数和选项。理解此语法将帮助您正确使用命令并避免混淆。

## 语法约定

命令概要使用特定格式来指示参数是必需还是可选，以及它们接受何种类型的值。

### 必需参数

不带方括号的参数是**必需**的，必须提供：

* **`<argument>`** - 必需的位置参数，需要一个值。
  * 示例：`<hook>` 表示你必须提供一个钩子名称
  * 用法：`wp cron event schedule my_hook`

* **`--option=<value>`** - 必需的选项，需要一个值。
  * 示例：`--dbname=<dbname>` 表示你必须提供数据库名称
  * 用法：`wp config create --dbname=mydatabase --dbuser=root`

### 可选参数

用方括号 **`[ ]`** 括起来的参数是可选的：

* **`[<argument>]`** - 一个可选的位置参数。
  * 示例：`[<next-run>]` 表示此参数可以省略
  * 如果省略，可能会使用默认值

* **`[--option=<value>]`** - 一个接受值的可选选项。
  * 示例：`[--dbhost=<dbhost>]` 表示此选项可以省略
  * 通常有默认值（例如，`--dbhost` 的默认值为 `localhost`）
  * 用法：`wp config create --dbname=mydb --dbuser=root --dbhost=127.0.0.1`

* **`[--flag]`** - 一个可选的布尔标志。
  * 示例：`[--force]` 表示此标志可以包含或省略
  * 当存在时，标志为 `true`；当不存在时，为 `false`
  * 用法：`wp config create --dbname=mydb --dbuser=root --force`

### 布尔标志

布尔标志是用于启用或禁用功能的开关：

* **启用**：包含标志以将其设置为 `true`
  * 示例：`--force` 启用强制模式

* **禁用**：大多数标志可以通过 `--no-` 前缀来“反转”
  * 示例：`--no-force` 显式禁用强制模式
  * 示例：`--no-color` 禁用彩色输出

### Associative Arguments

Some commands accept arbitrary key-value pairs:

* **`[--<field>=<value>]`** - Accepts any field name with a value.
  * Example: `--foo=bar --baz=qux`
  * Useful for passing custom data or configuration

### Repeatable Arguments

Arguments that can be provided multiple times:

* **`[--<field>=<value>]`** - When documented as repeatable, you can provide the option multiple times.
  * Example: `--require=<path>` can be used as `--require=/path/one.php --require=/path/two.php`

### Variadic Arguments

Arguments that accept multiple values:

* **`<argument>...`** - The ellipsis (`...`) indicates the argument accepts one or more values.
  * Example: `<file>...` means you can provide multiple files
  * Usage: `wp plugin install plugin1 plugin2 plugin3`

### 占位符说明

尖括号内的文本描述了期望接收的数值类型：

* **`<id>`** - 期望接收数字标识符
* **`<file>`** - 期望接收文件路径
* **`<url>`** - 期望接收 URL 地址
* **`<name>`** - 期望接收名称或标签
* **`<format>`** - 期望接收格式类型（通常会列出可用选项）

## 常见模式

### 必需的数据库连接

许多命令需要数据库连接信息：

```
--dbname=<dbname> --dbuser=<dbuser> [--dbpass=<dbpass>] [--dbhost=<dbhost>]
```

* `--dbname` 和 `--dbuser` 是必需的
* `--dbpass` 和 `--dbhost` 是可选的

### 格式选项

输出数据的命令通常接受格式选项：

```
[--format=<format>]
```

常见格式包括：`table`、`csv`、`json`、`yaml`、`count`

### 字段与筛选

处理多个字段的命令：

```
[--fields=<fields>] [--field=<field>]
```

* `--fields` 通常接受逗号分隔的列表
* `--field` 通常返回单个字段值

## 示例

以下是展示不同语法类型的实用示例：

```bash
# 必需参数（无括号）
wp config create --dbname=mydb --dbuser=root

# 带默认值的可选参数
wp config create --dbname=mydb --dbuser=root --dbhost=localhost

# 布尔标志
wp plugin install hello-dolly --activate --force

# 否定布尔标志
wp plugin list --no-color

# 关联参数
wp cron event schedule my_hook --foo=bar --baz=qux

# 多值参数
wp plugin install plugin1 plugin2 plugin3

# 带特定格式选项的可选字段
wp post list --format=json --fields=ID,post_title,post_date
```

## Tips

* Always check the command's `OPTIONS` section to see which arguments are required
* Use `wp help <command>` to see the complete synopsis and documentation
* When in doubt about a flag, try the `--help` option: `wp <command> --help`
* Default values for optional arguments are typically listed in the `OPTIONS` section
* Quote values that contain spaces or special characters: `--title="My Post Title"`

## 相关文档

* [文档标准](https://make.wordpress.org/cli/handbook/references/documentation-standards/) - 标注 WP-CLI 命令的标准
* [命令手册](https://make.wordpress.org/cli/handbook/guides/commands-cookbook/) - 命令如何工作
* [全局参数](https://make.wordpress.org/cli/handbook/references/config/) - 所有命令可用的参数