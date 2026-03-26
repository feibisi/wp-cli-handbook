---
title: "WP_CLI::launch_self()"
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

# WP_CLI::launch_self()

在新的进程中运行一个 WP-CLI 命令，并复用当前的运行时参数。

***

## 用法

    WP_CLI::launch_self( $command, $args = [], $assoc_args = [], $exit_on_error = true, $return_detailed = false, $runtime_args = [] )

<div>
<strong>$command</strong> (string) 要调用的 WP-CLI 命令。<br />
<strong>$args</strong> (array) 调用命令时要包含的位置参数。<br />
<strong>$assoc_args</strong> (array) 调用命令时要包含的关联参数。<br />
<strong>$exit_on_error</strong> (bool) 如果命令返回较高的返回码，是否退出。<br />
<strong>$return_detailed</strong> (bool) 是返回退出状态（默认）还是详细的执行结果。<br />
<strong>$runtime_args</strong> (array) 覆盖一个或多个全局参数（path,url,user,allow-root）<br />
<strong>@return</strong> (int|ProcessRun) 命令退出状态，或一个 ProcessRun 实例<br />
</div>


***

## 说明

请改用 `WP_CLI::runcommand()`，它更易于使用且效果更好。

注意：虽然此命令确实会保留一组有限的运行时参数，
但它*不会*保留环境变量。实际上，使用 WP_CLI::launch_self() 时不会加载 WP-CLI 包，
因为启动的进程无法访问当前进程的 $HOME。


*内部 API 文档是在每次发布时从 WP-CLI 代码库生成的。要提出改进建议，请提交一个拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-launch/">WP_CLI::launch()</a></strong> - 启动一个接管 I/O 的任意外部进程。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-runcommand/">WP_CLI::runcommand()</a></strong> - 运行一个 WP-CLI 命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-run-command/">WP_CLI::run_command()</a></strong> - 在当前进程内使用相同的全局参数运行给定的命令。</li>



</ul>