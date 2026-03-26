---
title: "When /^I (run|try) the previous command again$/"
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

# When /^I (run|try) the previous command again$/

再次运行或尝试运行上一条命令。

***

## 用法

`run` 期望退出码为 0，而 `try` 允许非零退出码。

```
场景：我的示例场景
  当 我运行 `wp site option update admin_user_id 1`
  那么 STDOUT 应包含：
    """
    Success: Updated 'admin_user_id' site option.
    """

  当 我再次运行上一条命令
  那么 STDOUT 应包含：
    """
    Success: Value passed for 'admin_user_id' site option is unchanged.
    """
```

*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*

***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-launch-in-the-background/">When /^I launch in the background `([^`]+)`$/</a></strong> - 在后台启动给定命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try/">When /^I (run|try) `([^`]+)`$/</a></strong> - 运行或尝试运行给定命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-from/">When /^I (run|try) `([^`]+)` from '([^\s]+)'$/</a></strong> - 在子目录中运行或尝试运行给定命令。</li>



</ul>