---
title: "Then /^(STDOUT|STDERR) should not be empty$/"
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

# Then /^(STDOUT|STDERR) should not be empty$/

期望 STDOUT 或 STDERR 不为空。


***

## 用法

```
Scenario: 我的示例场景
  When I run `wp user create examplejane jane@example.com`
  Then STDOUT should not be empty
```


*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-return-code-should-not-be/">Then /^the return code should( not)? be (\d+)$/</a></strong> - 期望上一个命令返回特定的退出码。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-strictly-be-contain-not-contain/">Then /^(STDOUT|STDERR) should( strictly)? (be|contain|not contain):$/</a></strong> - 检查 STDOUT 或 STDERR 的内容。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-number/">Then /^(STDOUT|STDERR) should be a number$/</a></strong> - 期望 STDOUT 或 STDERR 是一个数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-a-number/">Then /^(STDOUT|STDERR) should not be a number$/</a></strong> - 期望 STDOUT 或 STDERR 不是一个数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-table-containing-rows/">Then /^STDOUT should be a table containing rows:$/</a></strong> - 期望 STDOUT 是一个包含指定行的表格。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-end-with-a-table-containing-rows/">Then /^STDOUT should end with a table containing rows:$/</a></strong> - 期望 STDOUT 以一个包含指定行的表格结尾。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-json-containing/">Then /^STDOUT should be JSON containing:$/</a></strong> - 期望 STDOUT 包含有效的 JSON 输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-json-array-containing/">Then /^STDOUT should be a JSON array containing:$/</a></strong> - 期望 STDOUT 包含有效的 JSON 数组输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-csv-containing/">Then /^STDOUT should be CSV containing:$/</a></strong> - 期望 STDOUT 是包含特定值的 CSV。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-yaml-containing/">Then /^STDOUT should be YAML containing:$/</a></strong> - 期望 STDOUT 是包含特定内容的 YAML。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-empty/">Then /^(STDOUT|STDERR) should be empty$/</a></strong> - 期望 STDOUT 或 STDERR 为空。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-version-string-w/">Then /^(STDOUT|STDERR) should be a version string (&lt;|&lt;=|&gt;|&gt;=|==|=|!=|&lt;&gt;) ([+\w.{}-]+)$/</a></strong> - 期望 STDOUT 或 STDERR 是一个版本字符串，并与给定版本进行比较。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-file-directory-should-strictly-exist-not-exist-be-contain-not-contain/">Then /^the (.+) (file|directory) should( strictly)? (exist|not exist|be:|contain:|not contain:)$/</a></strong> - 期望某个文件或目录（不）存在或（不）包含特定内容。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-contents-of-the-file-should-not-match/">Then /^the contents of the (.+) file should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 使用正则表达式匹配文件内容。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-match/">Then /^(STDOUT|STDERR) should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 使用正则表达式匹配 STDOUT 或 STDERR。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-an-email-should-be-sent-not-be-sent/">Then /^an email should (be sent|not be sent)$/</a></strong> - 期望发送（或不发送）一封电子邮件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-http-status-code-should-be-code/">Then the HTTP status code should be :code</a></strong> - 期望访问 `http://localhost:8080` 时的 HTTP 状态码。</li>

</ul>