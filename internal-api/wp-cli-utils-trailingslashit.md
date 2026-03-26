---
title: "WP_CLI\Utils\trailingslashit()"
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

# WP_CLI\Utils\trailingslashit()

添加尾部斜杠。

***

## 用法

    WP_CLI\Utils\trailingslashit( $string )

<div>
<strong>$string</strong> (string) 需要添加尾部斜杠的字符串。<br />
<strong>@return</strong> (string) 添加了尾部斜杠的字符串。<br />
</div>


*内部 API 文档随每次发布从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*


***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-home-dir/">WP_CLI\Utils\get_home_dir()</a></strong> - 获取主目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-normalize-path/">WP_CLI\Utils\normalize_path()</a></strong> - 规范化文件系统路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-temp-dir/">WP_CLI\Utils\get_temp_dir()</a></strong> - 获取系统的临时目录。如果不可写，则警告用户。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-php-binary/">WP_CLI\Utils\get_php_binary()</a></strong> - 获取执行 WP-CLI 时使用的 PHP 二进制文件路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-php-binary/">WP_CLI::get_php_binary()</a></strong> - 获取执行 WP-CLI 时使用的 PHP 二进制文件路径。</li>



</ul>