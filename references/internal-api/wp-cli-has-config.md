---
title: "WP_CLI::has_config()"
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

# WP_CLI::has_config()

确认全局配置参数是否存在。

***

## 用法

    WP_CLI::has_config( $key )

<div>
<strong>$key</strong> (string) 要检查的配置参数键名。<br />
<strong>@return</strong> (bool) <br />
</div>


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-launch-editor-for-input/">WP_CLI\Utils\launch_editor_for_input()</a></strong> - 启动系统的 $EDITOR 供用户编辑文本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-flag-value/">WP_CLI\Utils\get_flag_value()</a></strong> - 返回标志值，若未设置则返回 $default 值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-report-batch-operation-results/">WP_CLI\Utils\report_batch_operation_results()</a></strong> - 报告对多个资源执行相同操作的结果。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-str-to-argv/">WP_CLI\Utils\parse_str_to_argv()</a></strong> - 将命令行参数字符串解析为类似 $argv 的变量。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-confirm/">WP_CLI::confirm()</a></strong> - 在执行破坏性操作前请求确认。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-read-value/">WP_CLI::read_value()</a></strong> - 从多种格式读取值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-config/">WP_CLI::get_config()</a></strong> - 获取全局配置参数的值。</li>



</ul>