---
title: "Behat 步骤"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - References
    - Repos
    - Data
---

# Behat 步骤

WP-CLI 使用基于 Behat 的测试框架，并提供一组自定义步骤定义来编写功能测试。

*Behat 步骤文档随每次版本发布从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

## Given

<ul>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-directory/">Given an empty directory</a></strong> - 创建一个空目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-non-existent-directory/">Given /^an? (empty|non-existent) ([^\s]+) directory$/</a></strong> - 创建或删除一个特定目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-cache/">Given an empty cache</a></strong> - 清空 WP-CLI 缓存目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-file-cache-file/">Given /^an? ([^\s]+) (file|cache file):$/</a></strong> - 使用给定内容创建一个文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-replaced-with-in-the-file/">Given /^&quot;([^&quot;]+)&quot; replaced with &quot;([^&quot;]+)&quot; in the ([^\s]+) file$/</a></strong> - 使用正则表达式在文件中搜索并替换字符串。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-that-http-requests-to-will-respond-with/">Given /^that HTTP requests to (.*?) will respond with:$/</a></strong> - 模拟对给定 URL 的 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-wp-files/">Given WP files</a></strong> - 下载 WordPress 文件但不安装。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-wp-config-php/">Given wp-config.php</a></strong> - 使用 `wp config create` 创建一个 wp-config.php 文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-database/">Given a database</a></strong> - 创建一个空数据库。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation/">Given a WP install(ation)</a></strong> - 安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-in-subdir/">Given a WP install(ation) in :subdir</a></strong> - 在给定目录中安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-with-composer/">Given a WP install(ation) with Composer</a></strong> - 使用 Composer 安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-with-composer-and-a-custom-vendor-directory-vendor-directory/">Given a WP install(ation) with Composer and a custom vendor directory :vendor_directory</a></strong> - 使用 Composer 和一个自定义的 vendor 目录安装 WordPress。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-multisite-subdirectory-subdomaininstall-installation/">Given /^a WP multisite (subdirectory|subdomain)?\s?(install|installation)$/</a></strong> - 安装 WordPress 多站点。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-these-installed-and-active-plugins/">Given these installed and active plugins:</a></strong> - 安装并激活一个或多个插件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-custom-wp-content-directory/">Given a custom wp-content directory</a></strong> - 配置自定义的 `wp-content` 目录。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-download/">Given download:</a></strong> - 将多个文件下载到指定目标位置。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-save-stdout-stderr-as/">Given /^save (STDOUT|STDERR) ([\'].+[^\'])?\s?as \{(\w+)\}$/</a></strong> - 将 STDOUT 或 STDERR 的内容存储到变量中。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-new-phar-with-the-same-version-version/">Given /^a new Phar with (?:the same version|version &quot;([^&quot;]+)&quot;)$/</a></strong> - 使用指定版本构建一个新的 WP-CLI Phar 文件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-downloaded-phar-with-the-same-version-version/">Given /^a downloaded Phar with (?:the same version|version &quot;([^&quot;]+)&quot;)$/</a></strong> - 从 GitHub 下载指定版本的 WP-CLI Phar 文件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-save-the-file-as/">Given /^save the (.+) file ([\'].+[^\'])?as \{(\w+)\}$/</a></strong> - 将指定文件的内容存储到变量中。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-misconfigured-wp-content-dir-constant-directory/">Given a misconfigured WP_CONTENT_DIR constant directory</a></strong> - 修改 wp-config.php 文件，将 `WP_CONTENT_DIR` 设置为空字符串。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-dependency-on-current-wp-cli/">Given a dependency on current wp-cli</a></strong> - 将 `wp-cli/wp-cli` 添加为 Composer 依赖项。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-php-built-in-web-server/">Given a PHP built-in web server</a></strong> - 在当前目录启动 PHP 内置 Web 服务器。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-php-built-in-web-server-to-serve-subdir/">Given a PHP built-in web server to serve :subdir</a></strong> - 在指定子目录中启动 PHP 内置 Web 服务器。</li>

</ul>

## When

<ul>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-launch-in-the-background/">When /^I launch in the background `([^`]+)`$/</a></strong> - 在后台启动给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try/">When /^I (run|try) `([^`]+)`$/</a></strong> - 运行或尝试给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-from/">When /^I (run|try) `([^`]+)` from '([^\s]+)'$/</a></strong> - 在子目录中运行或尝试给定的命令。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/when-i-run-try-the-previous-command-again/">When /^I (run|try) the previous command again$/</a></strong> - 再次运行或尝试上一个命令。</li>


</ul>

## Then

<ul>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-return-code-should-not-be/">Then /^the return code should( not)? be (\d+)$/</a></strong> - 期望上一个命令返回特定的退出码。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-strictly-be-contain-not-contain/">Then /^(STDOUT|STDERR) should( strictly)? (be|contain|not contain):$/</a></strong> - 检查 STDOUT 或 STDERR 的内容。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-number/">Then /^(STDOUT|STDERR) should be a number$/</a></strong> - 期望 STDOUT 或 STDERR 是数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-a-number/">Then /^(STDOUT|STDERR) should not be a number$/</a></strong> - 期望 STDOUT 或 STDERR 不是数值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-table-containing-rows/">Then /^STDOUT should be a table containing rows:$/</a></strong> - 期望 STDOUT 是一个包含给定行的表格。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-end-with-a-table-containing-rows/">Then /^STDOUT should end with a table containing rows:$/</a></strong> - 期望 STDOUT 以一个包含给定行的表格结尾。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-json-containing/">Then /^STDOUT should be JSON containing:$/</a></strong> - 期望 STDOUT 包含有效的 JSON 输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-a-json-array-containing/">Then /^STDOUT should be a JSON array containing:$/</a></strong> - 期望 STDOUT 包含有效的 JSON 数组输出。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-csv-containing/">Then /^STDOUT should be CSV containing:$/</a></strong> - 期望 STDOUT 是包含特定值的 CSV。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-should-be-yaml-containing/">Then /^STDOUT should be YAML containing:$/</a></strong> - 期望 STDOUT 是包含特定内容的 YAML。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-empty/">Then /^(STDOUT|STDERR) should be empty$/</a></strong> - 期望 STDOUT 或 STDERR 为空。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-be-empty/">Then /^(STDOUT|STDERR) should not be empty$/</a></strong> - 期望 STDOUT 或 STDERR 不为空。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-be-a-version-string-w/">Then /^(STDOUT|STDERR) should be a version string (&lt;|&lt;=|&gt;|&gt;=|==|=|!=|&lt;&gt;) ([+\w.{}-]+)$/</a></strong> - 期望 STDOUT 或 STDERR 是一个版本字符串，并与给定的版本进行比较。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-file-directory-should-strictly-exist-not-exist-be-contain-not-contain/">Then /^the (.+) (file|directory) should( strictly)? (exist|not exist|be:|contain:|not contain:)$/</a></strong> - 期望某个文件或目录（不）存在或（不）包含特定内容。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-contents-of-the-file-should-not-match/">Then /^the contents of the (.+) file should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 使用正则表达式匹配文件内容。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-stdout-stderr-should-not-match/">Then /^(STDOUT|STDERR) should( not)? match (((\/.+\/)|(#.+#))([a-z]+)?)$/</a></strong> - 使用正则表达式匹配 STDOUT 或 STDERR。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-an-email-should-be-sent-not-be-sent/">Then /^an email should (be sent|not be sent)$/</a></strong> - 期望发送（或不发送）一封电子邮件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/then-the-http-status-code-should-be-code/">Then the HTTP status code should be :code</a></strong> - 期望访问 `http://localhost:8080` 时的 HTTP 状态码。</li>

</ul>