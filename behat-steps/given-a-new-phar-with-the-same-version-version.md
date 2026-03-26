---
title: "给定 /^一个版本为 (?:相同版本|&quot;([^&quot;]+)&quot;) 的新 Phar 文件$/"
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

# 给定 /^一个版本为 (?:相同版本|&quot;([^&quot;]+)&quot;) 的新 Phar 文件$/

使用指定版本构建一个新的 WP-CLI Phar 文件。

***

## 用法

```
场景：我的示例场景
  给定一个空目录
  并且一个版本为 "2.11.0" 的新 Phar 文件
```

*Behat 步骤文档随每次 WP-CLI 代码库发布自动生成。如需改进建议，请提交拉取请求。*

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-directory/">Given an empty directory</a></strong> - 创建一个空目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-non-existent-directory/">Given /^an? (empty|non-existent) ([^\s]+) directory$/</a></strong> - 创建或删除一个特定目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-cache/">Given an empty cache</a></strong> - 清空 WP-CLI 缓存目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-file-cache-file/">Given /^an? ([^\s]+) (file|cache file):$/</a></strong> - 创建具有给定内容的文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-replaced-with-in-the-file/">Given /^&quot;([^&quot;]+)&quot; replaced with &quot;([^&quot;]+)&quot; in the ([^\s]+) file$/</a></strong> - 使用正则表达式在文件中搜索并替换字符串。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-that-http-requests-to-will-respond-with/">Given /^that HTTP requests to (.*?) will respond with:$/</a></strong> - 模拟对给定 URL 的 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-wp-files/">Given WP files</a></strong> - 下载 WordPress 文件但不安装。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-wp-config-php/">Given wp-config.php</a></strong> - 使用 `wp config create` 创建 wp-config.php 文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-database/">Given a database</a></strong> - 创建一个空数据库。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation/">Given /^a WP( \d[^\s]+)? install(?:ation)?$/</a></strong> - 安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-in/">Given /^a WP( [^\s]+)? install(?:ation)? in ['&quot;]?([^'&quot;]+)['&quot;]?$/</a></strong> - 在给定目录中安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-with-composer/">Given a WP install(ation) with Composer</a></strong> - 使用 Composer 安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-with-composer-and-a-custom-vendor-directory-vendor-directory/">Given a WP install(ation) with Composer and a custom vendor directory :vendor_directory</a></strong> - 使用 Composer 和自定义供应商目录安装 WordPress。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-multisite-subdirectory-subdomaininstall-installation/">Given /^a WP multisite (subdirectory|subdomain)?\s?(install|installation)$/</a></strong> - 安装 WordPress 多站点。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-these-installed-and-active-plugins/">Given these installed and active plugins:</a></strong> - 安装并激活一个或多个插件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-custom-wp-content-directory/">Given a custom wp-content directory</a></strong> - 配置自定义的 `wp-content` 目录。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-download/">Given download:</a></strong> - 将多个文件下载到指定目标位置。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-save-stdout-stderr-as/">Given /^save (STDOUT|STDERR) ([\'].+[^\'])?\s?as \{(\w+)\}$/</a></strong> - 将 STDOUT 或 STDERR 的内容存储到变量中。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-downloaded-phar-with-the-same-version-version/">Given /^a downloaded Phar with (?:the same version|version &quot;([^&quot;]+)&quot;)$/</a></strong> - 从 GitHub 下载特定版本的 WP-CLI Phar 文件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-save-the-file-as/">Given /^save the (.+) file ([\'].+[^\'])?as \{(\w+)\}$/</a></strong> - 将指定文件的内容存储到变量中。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-misconfigured-wp-content-dir-constant-directory/">Given a misconfigured WP_CONTENT_DIR constant directory</a></strong> - 修改 wp-config.php 文件，将 `WP_CONTENT_DIR` 设置为空字符串。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-dependency-on-current-wp-cli/">Given a dependency on current wp-cli</a></strong> - 将 `wp-cli/wp-cli` 添加为 Composer 依赖项。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-php-built-in-web-server/">Given a PHP built-in web server</a></strong> - 在当前目录启动 PHP 内置 Web 服务器。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-php-built-in-web-server-to-serve-subdir/">Given a PHP built-in web server to serve :subdir</a></strong> - 在指定子目录中启动 PHP 内置 Web 服务器。</li>

</ul>