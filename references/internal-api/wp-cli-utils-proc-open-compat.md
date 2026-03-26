---
title: "WP_CLI\Utils\proc_open_compat()"
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

# WP_CLI\Utils\proc_open_compat()

Windows 兼容的 `proc_open()`。解决 PHP 中的 bug，并处理类 Unix 的 `ENV_VAR=blah cmd` 环境变量前缀。

***

## 用法

    WP_CLI\Utils\proc_open_compat( $cmd, $descriptorspec, $pipes, $cwd = null, $env = null, $other_options = null )

<div>
<strong>$cmd</strong> (string) 要执行的命令。<br />
<strong>string&gt;</strong> (array&lt;int,) $descriptorspec 描述符编号及其值的索引数组。<br />
<strong>string&gt;</strong> (array&lt;int,) &$pipes         与 PHP 端创建的管道对应的文件指针索引数组。<br />
<strong>$cwd</strong> (string) 命令的初始工作目录。<br />
<strong>string&gt;</strong> (array&lt;string,) $env            环境变量数组。<br />
<strong>$other_options</strong> (array&lt;string&gt;) 附加选项数组（仅限 Windows）。<br />
<strong>@return</strong> (resource) 已去除任何环境变量设置的资源。<br />
</div>


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交 pull request。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-write-csv/">WP_CLI\Utils\write_csv()</a></strong> - 将数据以 CSV 格式写入给定文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-http-request/">WP_CLI\Utils\http_request()</a></strong> - 向远程 URL 发起 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-named-sem-ver/">WP_CLI\Utils\get_named_sem_ver()</a></strong> - 比较两个版本字符串以获取命名的语义版本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-ssh-url/">WP_CLI\Utils\parse_ssh_url()</a></strong> - 解析 SSH URL 以获取其主机、端口和路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-basename/">WP_CLI\Utils\basename()</a></strong> - 独立于区域设置的 basename() 版本</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-ispiped/">WP_CLI\Utils\isPiped()</a></strong> - 检查当前脚本的输出是 TTY 还是管道/重定向</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-esc-like/">WP_CLI\Utils\esc_like()</a></strong> - 在为 MySQL 准备之前，对 LIKE 特殊字符 % 和 _ 进行转义的前半部分。</li>



</ul>