---
title: "WP_CLI\Utils\parse_ssh_url()"
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

# WP_CLI\Utils\parse_ssh_url()

解析 SSH URL 获取主机、端口和路径信息。

***

## 使用方法

    WP_CLI\Utils\parse_ssh_url( $url, $component = -1 )

<div>
<strong>$url</strong> (string) <br />
<strong>$component</strong> (int) <br />
<strong>@return</strong> (mixed) <br />
</div>

***

## 说明

功能类似 parse_url()，但增加了对已定义 SSH 别名的支持。

```
主机名 或 主机名/wordpress路径 或 主机名:端口/wordpress路径
```

*内部 API 文档随每个版本从 WP-CLI 代码库自动生成。如需改进建议，请提交拉取请求。*

***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-write-csv/">WP_CLI\Utils\write_csv()</a></strong> - 将数据以 CSV 格式写入指定文件</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-http-request/">WP_CLI\Utils\http_request()</a></strong> - 向远程 URL 发起 HTTP 请求</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-named-sem-ver/">WP_CLI\Utils\get_named_sem_ver()</a></strong> - 比较两个版本字符串获取语义化版本名称</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-basename/">WP_CLI\Utils\basename()</a></strong> - 与区域设置无关的 basename() 版本</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-ispiped/">WP_CLI\Utils\isPiped()</a></strong> - 检测当前脚本输出是 TTY 还是管道/重定向</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-proc-open-compat/">WP_CLI\Utils\proc_open_compat()</a></strong> - Windows 兼容的 `proc_open()`。修复 PHP 中的错误，并处理类 Unix 的 `ENV_VAR=blah cmd` 环境变量前缀</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-esc-like/">WP_CLI\Utils\esc_like()</a></strong> - 为 MySQL 准备数据前，对 LIKE 特殊字符 % 和 _ 进行转义的前半部分操作</li>



</ul>