---
title: "默认的医生诊断检查"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Doctor
    - Guides
    - Repos
---

# 默认的医生诊断检查

尽管其强大之处在于[可自定义的能力](https://make.wordpress.org/cli/handbook/doctor-customize-config/)，`wp doctor` 仍包含一系列默认的诊断检查，这些检查被视为生产网站的建议。

使用 `wp doctor list` 查看这些默认检查：

<table>

<thead>

<tr>

<th>名称</th>

<th>描述</th>

</tr>

</thead>

<tbody>

<tr>

<td>autoload-options-size</td>

<td>当自动加载选项大小超过 900 kb 阈值时发出警告。</td>

</tr>

<tr>

<td>constant-savequeries-falsy</td>

<td>确认 SAVEQUERIES 常量的预期状态。</td>

</tr>

<tr>

<td>constant-wp-debug-falsy</td>

<td>确认 WP_DEBUG 常量的预期状态。</td>

</tr>

<tr>

<td>core-update</td>

<td>当有新的 WordPress 次要版本可用时报错；主要版本则发出警告。</td>

</tr>

<tr>

<td>core-verify-checksums</td>

<td>根据发布的校验和验证 WordPress 文件；失败时报错。</td>

</tr>

<tr>

<td>cron-count</td>

<td>当注册的定时任务总数超过 50 个时报错。</td>

</tr>

<tr>

<td>cron-duplicates</td>

<td>当注册的重复定时任务超过 10 个时报错。</td>

</tr>

<tr>

<td>file-eval</td>

<td>检查文件系统中是否存在正则表达式模式 `eval\(.*base64_decode\(.*` 的文件。</td>

</tr>

<tr>

<td>option-blog-public</td>

<td>确认 'blog_public' 选项的预期值。</td>

</tr>

<tr>

<td>plugin-active-count</td>

<td>当激活的插件超过 80 个时发出警告。</td>

</tr>

<tr>

<td>plugin-deactivated</td>

<td>当超过 40% 的插件处于停用状态时发出警告。</td>

</tr>

<tr>

<td>plugin-update</td>

<td>当有插件更新可用时发出警告。</td>

</tr>

<tr>

<td>theme-update</td>

<td>当有主题更新可用时发出警告。</td>

</tr>

</tbody>

</table>

进一步解释：

*   自动加载选项是在每次向 WordPress 发出请求时自动加载的选项。大小超过推荐阈值可能是更大问题的征兆。
*   因为 `SAVEQUERIES` 会导致 WordPress 为每个 SQL 查询保存一个回溯跟踪，这是一项开销很大的操作，所以不鼓励在生产环境中使用 `SAVEQUERIES`。
*   WordPress 次要版本通常是安全版本，应立即应用。

如果您[创建自定义的 `doctor.yml` 配置文件](https://make.wordpress.org/cli/handbook/doctor-customize-config/)，可以使用 `wp doctor list --config=<file>` 查看文件中列出的诊断检查。