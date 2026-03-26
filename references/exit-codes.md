---
title: "退出码"
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

# 退出码

WP-CLI 遵循广泛采用的 Unix 退出码约定：`0` 表示成功（命令的主要条件已满足），而非零值表示主要条件未满足。这可能代表操作错误（命令无法执行请求的操作）或调用脚本预期测试的预期否定结果（例如“未安装”）。调用 WP-CLI 命令的脚本可以检查退出码以决定继续、重试还是中止。

## 标准退出码

| 退出码 | 含义 |
|:----------|:--------|
| `0` | 命令成功完成。请求的操作按预期执行。 |
| `1` | 命令失败。WP-CLI 无法按预期执行操作（例如参数无效、未找到 WordPress、遇到致命错误）。 |

`WP_CLI::error()` ([文档](https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/)) 是报告失败并以代码 `1` 退出的常规方式。

当命令需要向调用脚本传达特定结果时，可以使用 `WP_CLI::halt()` ([文档](https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/)) 以特定的非零代码退出。

## 布尔结果命令的退出码

某些命令设计为通过退出码而非输出来直接传达二元结果。这些命令仍使用标准的 `0`/`1` 代码，但 `1` 表示“条件未满足”而非“操作错误”。例如：

* `wp plugin is-installed <plugin>` 如果插件已安装则以 `0` 退出，如果未安装则以 `1` 退出。
* `wp theme is-installed <theme>` 遵循相同模式。
* `wp core is-installed` 当 WordPress 已安装时以 `0` 退出，未安装时以 `1` 退出。

在以下情况下使用退出码 `1` 表示“条件未满足”（而非错误）：

1. 命令结果是二元的（通过/失败，找到/未找到）且旨在直接在 shell 条件中测试。
2. 意图已明确记录，以便脚本作者知道退出码携带结果含义，而非错误含义。

对于信息性而非确定性结果的条件（例如，查找不到任何项目的列表命令仍然是成功操作——它返回了一个空列表），**不要**返回非零退出码。

## 在脚本中使用退出码

由于 WP-CLI 使用标准退出码，您可以直接在 shell 条件中使用 WP-CLI 命令：

```bash
# 在尝试激活插件前检查其是否已安装
if wp plugin is-installed my-plugin; then
    wp plugin activate my-plugin
else
    echo "Plugin not installed"
    exit 1
fi
```

您还可以在任何 WP-CLI 命令后检查 `$?` 以确认是否成功：

```bash
wp core update
if [ "$?" -ne 0 ]; then
    echo "Update failed"
fi
```