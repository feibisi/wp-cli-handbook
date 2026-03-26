---
title: "When /^I (run|try) `([^`]+)`$/"
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

# When /^I (run|try) `([^`]+)`$/

运行或尝试执行给定的命令。


***

## 用法

`run` 期望退出码为 0，而 `try` 允许非零退出码。

因此，如果使用 `run` 且命令出错，该步骤将失败。

```
Scenario: 我的示例场景
  When I run `wp core version`
  Then STDOUT 应包含：
    """
    6.8
    """

Scenario: 我的另一个场景
  When I try `wp i18n make-pot foo bar/baz.pot`
  Then STDERR 应包含：
    """
    Error: Not a valid source directory.
    """
  And 返回码应为 1
```


*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-launch-in-the-background/">When /^I launch in the background `([^`]+)`$/</a></strong> - 在后台启动给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-from/">When /^I (run|try) `([^`]+)` from '([^\s]+)'$/</a></strong> - 在子目录中运行或尝试执行给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-the-previous-command-again/">When /^I (run|try) the previous command again$/</a></strong> - 再次运行或尝试执行上一个命令。</li>



</ul>