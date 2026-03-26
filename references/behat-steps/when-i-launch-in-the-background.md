---
title: "When /^I launch in the background `([^`]+)`$/"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Behat Steps
    - References
    - Repos
---

# When /^I launch in the background `([^`]+)`$/

在后台启动给定的命令。


***

## 用法

```
Scenario: My example scenario
  Given a WP install
  And I launch in the background `wp server --host=localhost --port=8181`
  ...
```


*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try/">When /^I (run|try) `([^`]+)`$/</a></strong> - 运行或尝试给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-from/">When /^I (run|try) `([^`]+)` from '([^\s]+)'$/</a></strong> - 在子目录中运行或尝试给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-the-previous-command-again/">When /^I (run|try) the previous command again$/</a></strong> - 再次运行或尝试上一个命令。</li>



</ul>