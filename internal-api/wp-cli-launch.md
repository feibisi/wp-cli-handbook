---
title: "WP_CLI::launch()"
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

# WP_CLI::launch()

启动一个接管 I/O 的任意外部进程。

***

## 用法

    WP_CLI::launch( $command, $exit_on_error = true, $return_detailed = false )

<div>
<strong>$command</strong> (string) 要启动的外部进程。<br />
<strong>$exit_on_error</strong> (boolean) 当命令返回较高退出码时是否退出。<br />
<strong>$return_detailed</strong> (boolean) 是否返回退出状态（默认）或详细的执行结果。<br />
<strong>@return</strong> (int|ProcessRun) 命令退出状态，或包含完整详情的 ProcessRun 对象。<br />
</div>

***

## 说明

```
# 当 PharData 不可用时，`wp core download` 回退到 `tar` 二进制程序
if ( ! class_exists( 'PharData' ) ) {
    $cmd = "tar xz --strip-components=1 --directory=%s -f $tarball";
    WP_CLI::launch( Utils\esc_cmd( $cmd, $dest ) );
    return;
}
```

*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*

***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-launch-self/">WP_CLI::launch_self()</a></strong> - 在新进程中运行 WP-CLI 命令，复用当前运行时参数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-runcommand/">WP_CLI::runcommand()</a></strong> - 运行一个 WP-CLI 命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-run-command/">WP_CLI::run_command()</a></strong> - 在当前进程中使用相同的全局参数运行给定命令。</li>



</ul>