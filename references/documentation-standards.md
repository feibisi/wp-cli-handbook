---
title: "文档标准"
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

# 文档标准

为促进 WP-CLI 命令间的统一性与一致性，我们制定了这些文档标准并鼓励您遵循。通用性是可用性的关键要素，因为它能降低在不同命令间切换时所需的认知负荷。

针对 WP-CLI 项目的拉取请求将依据这些标准进行审核。也请为您自定义的命令遵循这些标准。

### 命令注解

以下是 `wp cron event schedule` 命令的 PHPdoc 注解示例：

```
/**
 * 安排新的 cron 事件。
 *
 * ## 选项
 *
 * <hook>
 * : 钩子名称。
 *
 * [<next-run>]
 * : Unix 时间戳或与 `strtotime()` 兼容的英文文本日期时间描述。默认为当前时间。
 *
 * [<recurrence>]
 * : 事件应重复的频率。可用计划名称请参见 `wp cron schedule list`。默认为不重复。
 *
 * [--<field>=<value>]
 * : 事件的关联参数。
 *
 * ## 示例
 *
 *     # 安排新的 cron 事件。
 *     $ wp cron event schedule cron_test
 *     Success: Scheduled event with hook 'cron_test' for 2016-05-31 10:19:16 GMT.
 *
 *     # 安排每小时重复的新 cron 事件。
 *     $ wp cron event schedule cron_test now hourly
 *     Success: Scheduled event with hook 'cron_test' for 2016-05-31 10:20:32 GMT.
 *
 *     # 安排新的 cron 事件并传递关联参数。
 *     $ wp cron event schedule cron_test '+1 hour' --foo=1 --bar=2
 *     Success: Scheduled event with hook 'cron_test' for 2016-05-31 11:21:35 GMT.
 */
```

逐条解析此示例：

* "安排新的 cron 事件。" 是命令描述。命令描述应少于 50 个字符，并使用主动语态和现在时态书写。
* 选项部分应以 `## 选项` 开头。标题前后各保留一个空行。
* 每个选项的命名应简洁描述其用途。
* 示例部分应以 `## 示例` 开头。标题前后各保留一个空行。
* 每个示例前后各保留一个空行，以帮助视觉上区分每个独立示例。
* 每个示例应包含 3 个部分。
    - 描述
        + 必须以 `#` 加空格开头。
        + 句子应以大写字母开头。
        + 注释必须以句号、感叹号或问号结尾。
        + 例如：`# 创建数据库。`
    - 命令
        + 必须以 `$` 加空格开头。例如：`$ wp db create`
    - 示例输出
        + 保持输出内容完全一致。注意输出中的空格和缩进。例外：如果输出非常长，可以截断仅显示合适部分。
        + 例如：`Success: Database created.`
* 如果可能，每个命令至少保留两个示例。一个展示基本用法，另一个展示高级用法。用例越多越好。

有关 WP-CLI 如何理解 PHPdoc 的更多详细信息，请参阅 [命令手册](https://make.wordpress.org/cli/handbook/commands-cookbook/)。

### 类注释

对于表示子命令集合的类，我们建议使用类级别的注释来提供对该集合的介绍。

```
/**
 * 管理选项。
 *
 * ## 示例
 *
 *     # 获取站点 URL。
 *     $ wp option get siteurl
 *     http://example.com
 *
 *     # 添加选项。
 *     $ wp option add my_option foobar
 *     Success: Added 'my_option' option.
 *
 *     # 更新选项。
 *     $ wp option update my_option '{"foo": "bar"}' --format=json
 *     Success: Updated 'my_option' option.
 *
 *     # 删除选项。
 *     $ wp option delete my_option
 *     Success: Deleted 'my_option' option.
 */
```

* 类可以包含多个示例。请遵循命令文档中示例的标准。

### Messages within command execution

```
$ wp theme activate twentysixteen
Success: Switched to 'Twenty Sixteen' theme.
```

* Message must start with a capital letter.
    - Exception: When message starts with a special key and is wrapped with quotes. Eg - `'movie' is not a registered post type.`
* If single line message, it must end with `.`.
    - Exception: There should be no trailing character in the end when colon `:` is used like this. `Invalid ID: 123`
    - Exception: Message to display in progress bar can omit trailing period. Eg - `Generating comments`
* Filenames and folder names must be wrapped with quotes ( `'` ).
* Roles, sidebar ID, post type key, taxonomy key must be wrapped with quotes.
* Message in the context of ongoing action could end with `...`. Eg - `Downloading from https://github.com/wp-cli/wp-cli/releases/download/v0.23.1/wp-cli-0.23.1.phar...`

### 命令参数说明

如果命令参数有一组允许的值，我们为默认值和可用选项设置了特殊格式（主要类似于 YAML）。

```
[--format=<format>]
: 以特定格式渲染输出。
---
default: table
options:
  - table
  - csv
  - json
  - count
  - yaml
---
```

* 区块以参数描述下方单独一行的 `---` 开始。
* 下一行使用 `default: value` 指定默认值。
* 对于选项，在下一行以 `options:` 开始。
* 按以下模式列出值：2 个空格，`-`，1 个空格，值
* 以 `---` 结束区块。