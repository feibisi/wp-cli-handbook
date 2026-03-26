---
title: "WP_CLI\Utils\isPiped()"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Internal Api
    - References
    - Repos
---

# WP_CLI\Utils\isPiped()

检查当前脚本的输出是 TTY 还是管道/重定向

***

## 用法

    WP_CLI\Utils\isPiped()

<div>
<strong>@return</strong> (bool) <br />
</div>


***

## 说明

如果 `STDOUT` 输出被重定向到管道或文件，则返回 `true`；如果输出直接发送到终端，则返回 `false`。

如果存在环境变量 `SHELL_PIPE`，返回结果将取决于其值。接受可验证为布尔值的字符串，如 `1`、`0`、`yes`、`no`。

即使 shell 被管道传输，也要启用 ASCII 格式化，请使用环境变量 `SHELL_PIPE=0`。
```
SHELL_PIPE=0 wp plugin list | cat
```

请注意，db 命令会转发到 mysql 客户端，该客户端不知道此环境变量。对于 db 命令，请改用 `--table` 选项。
```
wp db query --table "SELECT 1" | cat
```


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。要提出改进建议，请提交 pull request。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-write-csv/">WP_CLI\Utils\write_csv()</a></strong> - 将数据作为 CSV 写入给定文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-http-request/">WP_CLI\Utils\http_request()</a></strong> - 向远程 URL 发出 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-named-sem-ver/">WP_CLI\Utils\get_named_sem_ver()</a></strong> - 比较两个版本字符串以获取命名的语义版本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-ssh-url/">WP_CLI\Utils\parse_ssh_url()</a></strong> - 解析 SSH URL 以获取其主机、端口和路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-basename/">WP_CLI\Utils\basename()</a></strong> - 与区域设置无关的 basename() 版本</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-proc-open-compat/">WP_CLI\Utils\proc_open_compat()</a></strong> - Windows 兼容的 `proc_open()`。解决 PHP 中的错误，并处理类 Unix 的 `ENV_VAR=blah cmd` 环境变量前缀。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-esc-like/">WP_CLI\Utils\esc_like()</a></strong> - 在为 MySQL 准备之前，转义 LIKE 特殊字符 % 和 _ 的前半部分。</li>



</ul>