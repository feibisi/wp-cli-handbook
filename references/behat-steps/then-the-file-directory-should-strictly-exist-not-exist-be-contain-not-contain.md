---
title: "Then /^the (.+) (file|directory) should( strictly)? (exist|not exist|be:|contain:|not contain:)$/"
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

# Then /^the (.+) (file|directory) should( strictly)? (exist|not exist|be:|contain:|not contain:)$/

期望某个文件或目录（不）存在，或（不）包含特定内容。


***

## 用法

```
Scenario: 我的示例场景
  When I run `wp core download`
  Then the wp-settings.php file should exist
  And the wp-content directory should exist
  And the {RUN_DIR} directory should contain:
    """
    index.php
    license.txt
    """
  And the wp-config.php file should contain:
    """
    That's all, stop editing! Happy publishing.
    """
```


*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-return-code-should-not-be/">Then /^the return code should( not)? be (\d+)$/</a></strong> - 期望上一个命令返回特定的退出码。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-strictly-be-contain-not-contain/">Then /^(STDOUT|STDERR) should( strictly)? (be|contain|not contain):$/</a></strong> - 检查 STDOUT 或 STDERR 的内容。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-number/">Then /^(STDOUT|STDERR) should be a number$/</a></strong> - 期望 STDOUT 或 STDERR 是一个数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-a-number/">Then /^(STDOUT|STDERR) should not be a number$/</a></strong> - 期望 STDOUT 或 STDERR 不是一个数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-table-containing-rows/">Then /^STDOUT should be a table containing rows:$/</a></strong> - 期望 STDOUT 是一个包含给定行的表格。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-end-with-a-table-containing-rows/">Then /^STDOUT should end with a table containing rows:$/</a></strong> - 期望 STDOUT 以一个包含给定行的表格结尾。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-json-containing/">Then /^STDOUT should be JSON containing:$/</a></strong> - 期望 STDOUT 中包含有效的 JSON 输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-json-array-containing/">Then /^STDOUT should be a JSON array containing:$/</a></strong> - 期望 STDOUT 中包含有效的 JSON 数组输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-csv-containing/">Then /^STDOUT should be CSV containing:$/</a></strong> - 期望 STDOUT 是包含特定值的 CSV。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-yaml-containing/">Then /^STDOUT should be YAML containing:$/</a></strong> - 期望 STDOUT 是包含特定内容的 YAML。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-empty/">Then /^(STDOUT|STDERR) should be empty$/</a></strong> - 期望 STDOUT 或 STDERR 为空。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-empty/">Then /^(STDOUT|STDERR) should not be empty$/</a></strong> - 期望 STDOUT 或 STDERR 不为空。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-version-string-w/">Then /^(STDOUT|STDERR) should be a version string (&lt;|&lt;=|&gt;|&gt;=|==|=|!=|&lt;&gt;) ([+\w.{}-]+)$/</a></strong> - 期望 STDOUT 或 STDERR 是一个版本字符串，并与给定的版本进行比较。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-contents-of-the-file-should-not-match/">Then /^the contents of the (.+) file should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 将文件内容与正则表达式进行匹配。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-match/">Then /^(STDOUT|STDERR) should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 将 STDOUT 或 STDERR 与正则表达式进行匹配。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-an-email-should-be-sent-not-be-sent/">Then /^an email should (be sent|not be sent)$/</a></strong> - 期望发送（或不发送）一封电子邮件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-http-status-code-should-be-code/">Then the HTTP status code should be :code</a></strong> - 期望访问 `http://localhost:8080` 时的 HTTP 状态码。</li>

</ul>