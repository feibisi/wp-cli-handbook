---
title: "WP_CLI\Utils\normalize_path()"
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

# WP_CLI\Utils\normalize_path()

规范化文件系统路径。

***

## 用法

    WP_CLI\Utils\normalize_path( $path )

<div>
<strong>$path</strong> (string) 需要规范化的路径。<br />
<strong>@return</strong> (string) 路径。<br />
</div>

***

## 说明

在 Windows 系统上，将反斜杠替换为正斜杠，
并强制将驱动器字母转换为大写。
允许 Windows 网络共享路径以两个前导斜杠开头，
但确保所有其他重复的斜杠被缩减为单个斜杠。
确保 Windows 系统上的驱动器字母为大写。

*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-home-dir/">WP_CLI\Utils\get_home_dir()</a></strong> - 获取主目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-trailingslashit/">WP_CLI\Utils\trailingslashit()</a></strong> - 添加尾部斜杠。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-temp-dir/">WP_CLI\Utils\get_temp_dir()</a></strong> - 获取系统的临时目录。如果不可写，则警告用户。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-php-binary/">WP_CLI\Utils\get_php_binary()</a></strong> - 获取执行 WP-CLI 时使用的 PHP 二进制文件路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-php-binary/">WP_CLI::get_php_binary()</a></strong> - 获取执行 WP-CLI 时使用的 PHP 二进制文件路径。</li>



</ul>