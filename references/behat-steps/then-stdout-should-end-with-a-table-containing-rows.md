---
title: "Then /^STDOUT should end with a table containing rows:$/"
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

# Then /^STDOUT should end with a table containing rows:$/

期望 STDOUT 以包含指定行的表格结尾。

***

## 用法

当表格前有其他输出内容时很有用。

```
场景：我的示例场景
  假设有一个 WordPress 安装
  当我运行 `wp search-replace foo bar --report-changed-only`
  那么 STDOUT 应包含：
    """
    成功：完成 3 处替换。
    """
  并且 STDOUT 应以包含以下行的表格结尾：
    | 表名        | 列名         | 替换次数 | 类型 |
    | wp_options  | option_value | 1        | PHP  |
    | wp_postmeta | meta_value   | 1        | SQL  |
    | wp_posts    | post_title   | 1        | SQL  |
```


*Behat 步骤文档随每次 WP-CLI 版本发布从代码库自动生成。如需改进建议，请提交拉取请求。*

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-return-code-should-not-be/">Then /^the return code should( not)? be (\d+)$/</a></strong> - 期望前一个命令返回特定的退出码。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-strictly-be-contain-not-contain/">Then /^(STDOUT|STDERR) should( strictly)? (be|contain|not contain):$/</a></strong> - 检查 STDOUT 或 STDERR 的内容。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-number/">Then /^(STDOUT|STDERR) should be a number$/</a></strong> - 期望 STDOUT 或 STDERR 是数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-a-number/">Then /^(STDOUT|STDERR) should not be a number$/</a></strong> - 期望 STDOUT 或 STDERR 不是数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-table-containing-rows/">Then /^STDOUT should be a table containing rows:$/</a></strong> - 期望 STDOUT 是一个包含指定行的表格。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-json-containing/">Then /^STDOUT should be JSON containing:$/</a></strong> - 期望 STDOUT 包含有效的 JSON 输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-json-array-containing/">Then /^STDOUT should be a JSON array containing:$/</a></strong> - 期望 STDOUT 包含有效的 JSON 数组输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-csv-containing/">Then /^STDOUT should be CSV containing:$/</a></strong> - 期望 STDOUT 是包含特定值的 CSV。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-yaml-containing/">Then /^STDOUT should be YAML containing:$/</a></strong> - 期望 STDOUT 是包含特定内容的 YAML。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-empty/">Then /^(STDOUT|STDERR) should be empty$/</a></strong> - 期望 STDOUT 或 STDERR 为空。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-empty/">Then /^(STDOUT|STDERR) should not be empty$/</a></strong> - 期望 STDOUT 或 STDERR 不为空。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-version-string-w/">Then /^(STDOUT|STDERR) should be a version string (&lt;|&lt;=|&gt;|&gt;=|==|=|!=|&lt;&gt;) ([+\w.{}-]+)$/</a></strong> - 期望 STDOUT 或 STDERR 是一个版本字符串，并与给定版本进行比较。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-file-directory-should-strictly-exist-not-exist-be-contain-not-contain/">Then /^the (.+) (file|directory) should( strictly)? (exist|not exist|be:|contain:|not contain:)$/</a></strong> - 期望某个文件或目录（不）存在或（不）包含特定内容。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-contents-of-the-file-should-not-match/">Then /^the contents of the (.+) file should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 使用正则表达式匹配文件内容。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-match/">Then /^(STDOUT|STDERR) should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 使用正则表达式匹配 STDOUT 或 STDERR。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-an-email-should-be-sent-not-be-sent/">Then /^an email should (be sent|not be sent)$/</a></strong> - 期望发送（或不发送）一封电子邮件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-http-status-code-should-be-code/">Then the HTTP status code should be :code</a></strong> - 期望访问 `http://localhost:8080` 时的 HTTP 状态码。</li>

</ul>