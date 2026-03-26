---
title: "When /^I (run|try) `([^`]+)` from '([^\s]+)'$/"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Behat Steps
    - Repos
    - Data
---

# When /^I (run|try) `([^`]+)` from '([^\s]+)'$/

在子目录中运行或尝试执行给定的命令。


***

## 用法

`run` 期望退出码为 0，而 `try` 允许非零退出码。

```
Scenario: 我的示例场景
  When I run `wp core is-installed`
  Then STDOUT should be empty

  When I run `wp core is-installed` from 'foo/wp-content'
  Then STDOUT should be empty
```


*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交一个拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-launch-in-the-background/">When /^I launch in the background `([^`]+)`$/</a></strong> - 在后台启动给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try/">When /^I (run|try) `([^`]+)`$/</a></strong> - 运行或尝试执行给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-the-previous-command-again/">When /^I (run|try) the previous command again$/</a></strong> - 再次运行或尝试执行之前的命令。</li>



</ul>