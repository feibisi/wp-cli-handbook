---
title: "给定一个使用 Composer 且具有自定义供应商目录 :vendor_directory 的 WP 安装"
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

# 给定一个使用 Composer 且具有自定义供应商目录 :vendor_directory 的 WP 安装

使用 Composer 和自定义供应商目录安装 WordPress。


***

## 用法

```
场景：我的示例场景
  给定一个使用 Composer 且具有自定义供应商目录 'vendor-custom' 的 WP 安装
  ...

场景：我的其他场景
  给定一个使用 Composer 且具有自定义供应商目录 'vendor-custom' 的 WP 安装
  ...
```


*Behat 步骤文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-directory/">Given an empty directory</a></strong> - 创建一个空目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-non-existent-directory/">Given /^an? (empty|non-existent) ([^\s]+) directory$/</a></strong> - 创建或删除一个指定的目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-empty-cache/">Given an empty cache</a></strong> - 清空 WP-CLI 缓存目录。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-an-file-cache-file/">Given /^an? ([^\s]+) (file|cache file):$/</a></strong> - 创建具有给定内容的文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-replaced-with-in-the-file/">Given /^&quot;([^&quot;]+)&quot; replaced with &quot;([^&quot;]+)&quot; in the ([^\s]+) file$/</a></strong> - 使用正则表达式在文件中搜索并替换字符串。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-that-http-requests-to-will-respond-with/">Given /^that HTTP requests to (.*?) will respond with:$/</a></strong> - 模拟对给定 URL 的 HTTP 请求。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-wp-files/">Given WP files</a></strong> - 下载 WordPress 文件但不安装。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-wp-config-php/">Given wp-config.php</a></strong> - 使用 `wp config create` 创建 wp-config.php 文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-database/">Given a database</a></strong> - 创建一个空数据库。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation/">Given /^a WP( \d[^\s]+)? install(?:ation)?$/</a></strong> - 安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-in/">Given /^a WP( [^\s]+)? install(?:ation)? in ['&quot;]?([^'&quot;]+)['&quot;]?$/</a></strong> - 在指定目录中安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-installation-with-composer/">Given a WP install(ation) with Composer</a></strong> - 使用 Composer 安装 WordPress。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-wp-multisite-subdirectory-subdomaininstall-installation/">Given /^a WP multisite (subdirectory|subdomain)?\s?(install|installation)$/</a></strong> - 安装 WordPress 多站点。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-these-installed-and-active-plugins/">Given these installed and active plugins:</a></strong> - 安装并激活一个或多个插件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-custom-wp-content-directory/">给定一个自定义的 wp-content 目录</a></strong> - 配置一个自定义的 `wp-content` 目录。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-download/">给定下载：</a></strong> - 将多个文件下载到指定的目标位置。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-save-stdout-stderr-as/">给定 /^保存 (STDOUT|STDERR) ([\'].+[^\'])?\s?为 \{(\w+)\}$/</a></strong> - 将 STDOUT 或 STDERR 的内容存储在一个变量中。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-new-phar-with-the-same-version-version/">给定 /^一个具有（相同版本|版本 &quot;([^&quot;]+)&quot;）的新 Phar$/</a></strong> - 使用指定版本构建一个新的 WP-CLI Phar 文件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-downloaded-phar-with-the-same-version-version/">给定 /^一个具有（相同版本|版本 &quot;([^&quot;]+)&quot;）的已下载 Phar$/</a></strong> - 从 GitHub 下载特定版本的 WP-CLI Phar 文件。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-save-the-file-as/">给定 /^将 (.+) 文件 ([\'].+[^\'])?保存为 \{(\w+)\}$/</a></strong> - 将指定文件的内容存储在一个变量中。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-misconfigured-wp-content-dir-constant-directory/">给定一个配置错误的 WP_CONTENT_DIR 常量目录</a></strong> - 修改 wp-config.php 文件，将 `WP_CONTENT_DIR` 设置为空字符串。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-dependency-on-current-wp-cli/">给定对当前 wp-cli 的依赖</a></strong> - 将 `wp-cli/wp-cli` 添加为 Composer 依赖项。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-php-built-in-web-server/">给定一个 PHP 内置 Web 服务器</a></strong> - 在当前目录启动一个 PHP 内置 Web 服务器。</li>

<li><strong><a href="https://make.wordpress.org/cli/handbook/behat-steps/given-a-php-built-in-web-server-to-serve-subdir/">给定一个 PHP 内置 Web 服务器来服务 :subdir</a></strong> - 在指定的子目录中启动一个 PHP 内置 Web 服务器。</li>

</ul>