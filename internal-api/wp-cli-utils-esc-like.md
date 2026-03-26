---
title: "WP_CLI\Utils\esc_like()"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Internal Api
    - Repos
    - Data
---

# WP_CLI\Utils\esc_like()

在准备 MySQL 查询前，对 LIKE 特殊字符 % 和 _ 进行转义的前半部分操作。

***

## 用法

    WP_CLI\Utils\esc_like( $text )

<div>
<strong>$text</strong> (string) 需要转义的原始文本。用户输入的文本不应包含<br />                    额外添加或删除的反斜杠。<br />
<strong>@return</strong> (string) 返回 LIKE 短语形式的字符串。输出结果并非 SQL 安全，需随后调用 $wpdb::prepare()<br />               或 real_escape 函数。<br />
</div>

***

## 说明

仅在 wpdb::prepare() 或 esc_sql() 之前使用此函数。颠倒顺序会严重危害安全性。

代码复制自核心文件 "wp-includes/wp-db.php"。避免依赖 WP 4.4 版本的 wpdb。

*内部 API 文档随每次版本发布从 WP-CLI 代码库自动生成。如需改进建议，请提交拉取请求。*

***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-write-csv/">WP_CLI\Utils\write_csv()</a></strong> - 将数据以 CSV 格式写入指定文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-http-request/">WP_CLI\Utils\http_request()</a></strong> - 向远程 URL 发起 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-named-sem-ver/">WP_CLI\Utils\get_named_sem_ver()</a></strong> - 比较两个版本字符串以获取命名的语义化版本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-ssh-url/">WP_CLI\Utils\parse_ssh_url()</a></strong> - 解析 SSH 网址获取主机、端口和路径信息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-basename/">WP_CLI\Utils\basename()</a></strong> - 与区域设置无关的 basename() 版本</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-ispiped/">WP_CLI\Utils\isPiped()</a></strong> - 检测当前脚本的输出是 TTY 还是管道/重定向</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-proc-open-compat/">WP_CLI\Utils\proc_open_compat()</a></strong> - Windows 兼容的 `proc_open()`。修复 PHP 中的错误，并处理类 Unix 系统 `ENV_VAR=blah cmd` 形式的环境变量前缀。</li>



</ul>