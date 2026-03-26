---
title: "WP_CLI::run_command()"
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

# WP_CLI::run_command()

在当前进程中使用相同的全局参数运行指定命令。

***

## 用法

    WP_CLI::run_command( $args, $assoc_args = [] )

<div>
<strong>$args</strong> (array) 包含命令名的位置参数。<br />
<strong>$assoc_args</strong> (array) <br />
</div>

***

## 说明

建议改用 `WP_CLI::runcommand()`，它更易用且效果更好。

若要在新进程中使用相同全局参数运行命令，请使用 WP_CLI::launch_self()。
若要在新进程中使用不同全局参数运行命令，请使用 WP_CLI::launch()。

```
ob_start();
WP_CLI::run_command( array( 'cli', 'cmd-dump' ) );
$ret = ob_get_clean();
```

*内部 API 文档随每个版本从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

***

## 相关方法

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-launch/">WP_CLI::launch()</a></strong> - 启动一个接管 I/O 的任意外部进程。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-launch-self/">WP_CLI::launch_self()</a></strong> - 在新进程中复用当前运行时参数运行 WP-CLI 命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-runcommand/">WP_CLI::runcommand()</a></strong> - 运行 WP-CLI 命令。</li>



</ul>