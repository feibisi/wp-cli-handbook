---
title: "WP_CLI\Utils\get_named_sem_ver()"
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

# WP_CLI\Utils\get_named_sem_ver()

比较两个版本字符串以获取命名的语义版本。

***

## 用法

    WP_CLI\Utils\get_named_sem_ver( $new_version, $original_version )

<div>
<strong>$new_version</strong> (string) <br />
<strong>$original_version</strong> (string) <br />
<strong>@return</strong> (string) 'minor', 'patch'<br />
</div>


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-write-csv/">WP_CLI\Utils\write_csv()</a></strong> - 将数据以 CSV 格式写入指定文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-http-request/">WP_CLI\Utils\http_request()</a></strong> - 向远程 URL 发起 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-ssh-url/">WP_CLI\Utils\parse_ssh_url()</a></strong> - 解析 SSH URL 以获取其主机、端口和路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-basename/">WP_CLI\Utils\basename()</a></strong> - 与区域设置无关的 basename() 版本</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-ispiped/">WP_CLI\Utils\isPiped()</a></strong> - 检查当前脚本的输出是 TTY 还是管道/重定向</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-proc-open-compat/">WP_CLI\Utils\proc_open_compat()</a></strong> - Windows 兼容的 `proc_open()`。解决 PHP 中的错误，并处理类 Unix 的 `ENV_VAR=blah cmd` 环境变量前缀。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-esc-like/">WP_CLI\Utils\esc_like()</a></strong> - 在为 MySQL 准备之前，对 LIKE 特殊字符 % 和 _ 进行转义的前半部分。</li>



</ul>