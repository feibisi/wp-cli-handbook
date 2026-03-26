---
title: "WP_CLI\Utils\http_request()"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Internal Api
    - References
    - Repos
---

# WP_CLI\Utils\http_request()

Make a HTTP request to a remote URL.

***

## Usage

    WP_CLI\Utils\http_request( $method, $url, $data = null, $headers = [], $options = [] )

<div>
<strong>$method</strong> (string) HTTP method (GET, POST, DELETE, etc.).<br />
<strong>$url</strong> (string) URL to make the HTTP request to.<br />
<strong>$data</strong> (array|null) Data to send either as a query string for GET/HEAD requests,<br />
<strong>$headers</strong> (array) Add specific headers to the request.<br />
<strong>$options</strong> (array) {<br />    Optional. An associative array of additional request options.<br />    @type bool $halt_on_error Whether or not command execution should be halted on error. Default: true<br />    @type bool|string $verify A boolean to use enable/disable SSL verification<br />                              or string absolute path to CA cert to use.<br />                              Defaults to detected CA cert bundled with the Requests library.<br />    @type bool $insecure      Whether to retry automatically without certificate validation.<br />}<br />
<strong>@return</strong> (object) <br />
</div>


***

## Notes

Wraps the Requests HTTP library to ensure every request includes a cert.

```
# `wp core download` verifies the hash for a downloaded WordPress archive

$md5_response = Utils\http_request( 'GET', $download_url . '.md5' );
if ( 20 != substr( $md5_response->status_code, 0, 2 ) ) {
     WP_CLI::error( "Couldn't access md5 hash for release (HTTP code {$response->status_code})" );
}
```
                           or in the body for POST requests.


*Internal API documentation is generated from the WP-CLI codebase on every release. To suggest improvements, please submit a pull request.*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-write-csv/">WP_CLI\Utils\write_csv()</a></strong> - 将数据以 CSV 格式写入指定文件。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-named-sem-ver/">WP_CLI\Utils\get_named_sem_ver()</a></strong> - 比较两个版本字符串以获取命名的语义化版本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-ssh-url/">WP_CLI\Utils\parse_ssh_url()</a></strong> - 解析 SSH URL 以获取其主机、端口和路径。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-basename/">WP_CLI\Utils\basename()</a></strong> - 与区域设置无关的 basename() 版本</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-ispiped/">WP_CLI\Utils\isPiped()</a></strong> - 检查当前脚本的输出是 TTY 还是管道/重定向</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-proc-open-compat/">WP_CLI\Utils\proc_open_compat()</a></strong> - Windows 兼容的 `proc_open()`。解决 PHP 中的错误，并处理类 Unix 的 `ENV_VAR=blah cmd` 环境变量前缀。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-esc-like/">WP_CLI\Utils\esc_like()</a></strong> - 在为 MySQL 准备之前，转义 LIKE 特殊字符 % 和 _ 的前半部分。</li>



</ul>