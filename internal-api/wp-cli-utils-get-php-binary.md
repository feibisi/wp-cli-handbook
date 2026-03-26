---
title: "WP_CLI\Utils\get_php_binary()"
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

# WP_CLI\Utils\get_php_binary()

获取执行 WP-CLI 时使用的 PHP 二进制文件路径。

***

## 用法

    WP_CLI\Utils\get_php_binary()

<div>
<strong>@return</strong> (string) <br />
</div>


***

## 说明

环境变量允许指定特定的二进制文件。


*内部 API 文档随每次发布从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*


***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-home-dir/">WP_CLI\Utils\get_home_dir()</a></strong> - 获取主目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-trailingslashit/">WP_CLI\Utils\trailingslashit()</a></strong> - 追加尾部斜杠。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-normalize-path/">WP_CLI\Utils\normalize_path()</a></strong> - 规范化文件系统路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-temp-dir/">WP_CLI\Utils\get_temp_dir()</a></strong> - 获取系统临时目录。如果不可写则警告用户。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-php-binary/">WP_CLI::get_php_binary()</a></strong> - 获取执行 WP-CLI 时使用的 PHP 二进制文件路径。</li>



</ul>