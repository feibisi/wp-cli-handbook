---
title: "配置"
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

# 配置

WP-CLI 拥有一系列适用于所有命令的全局参数（例如 `--path=<path>` 和 `--user=<user>`）。它们被称为*全局参数*，因为它们影响 WP-CLI 与 WordPress 的交互方式，并且所有命令中的行为都相同。

```
# `--user=<user>` 将请求设置为特定的 WordPress 用户
$ wp --user=wpcli eval 'echo wp_get_current_user()->user_email;'
wpcli@example.com
```

对于重复使用，WP-CLI 还可以从 YAML 配置文件（例如 `wp-cli.yml`）中读取选项。WP-CLI 会根据下面定义的规则自动发现文件系统中的配置文件。这些配置文件可以指定全局参数和子命令特定参数的默认值。

```
# WordPress develop 包含一个 `wp-cli.yml` 文件，以便轻松使用 WP-CLI
$ pwd
/srv/www/wordpress-develop.dev
$ cat wp-cli.yml
path: src/
```

参数按照优先级顺序解释，从最高优先级到最低优先级：

1. 命令行参数。
1. 当前工作目录（或向上）中的 `wp-cli.local.yml` 文件。
1. 当前工作目录（或向上）中的 `wp-cli.yml` 文件。
1. `~/.wp-cli/config.yml` 文件（路径可以通过设置 `WP_CLI_CONFIG_PATH` 环境变量来更改）。
1. WP-CLI 默认值。

## 全局参数

下表列出了可用的 <span class="argument">参数</span>（在命令行中指定）和 <span class="option">选项</span>（在配置文件中指定）。

<table>
	<thead>
	<tr>
		<th>描述</th>
		<th><span class="argument">参数</span></th>
		<th><span class="option">选项</span></th>
	</tr>
	</thead>
	<tbody>
		<tr>
		<td>
			WordPress 文件的路径。
			<br />
			默认值：<code>null</code>
		</td>
		<td>
			<code class="flag">--path=&lt;path&gt;</code>
		</td>
		<td>
			<code class="option">path: &lt;path&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			通过 SSH 对远程服务器执行操作。
			<br />
			默认值：<code>null</code>
		</td>
		<td>
			<code class="flag">--ssh=[&lt;user&gt;@]&lt;host&gt;[:&lt;port&gt;][&lt;path&gt;]</code>
		</td>
		<td>
			<code class="option">ssh: [&lt;user&gt;@]&lt;host&gt;[:&lt;port&gt;][&lt;path&gt;]</code>
		</td>
	</tr>
	<tr>
		<td>
			通过 HTTP 对远程 WordPress 安装执行操作。
			<br />
			默认值：<code>null</code>
		</td>
		<td>
			<code class="flag">--http=&lt;http&gt;</code>
		</td>
		<td>
			<code class="option">http: &lt;http&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			伪装请求来自给定的 URL。在多站点中，此参数用于指定目标站点。
			<br />
			默认值：<code>null</code>
		</td>
		<td>
			<code class="flag">--url=&lt;url&gt;</code>
		</td>
		<td>
			<code class="option">url: &lt;url&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			设置 WordPress 用户。
			<br />
			默认值：<code>null</code>
		</td>
		<td>
			<code class="flag">--user=&lt;id|login|email&gt;</code>
		</td>
		<td>
			<code class="option">user: &lt;id|login|email&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			跳过加载所有或部分插件。注意：mu-plugins 仍会被加载。
			<br />
			默认值：<code>&quot;&quot;</code>
		</td>
		<td>
			<code class="flag">--skip-plugins[=&lt;plugin&gt;]</code>
		</td>
		<td>
			<code class="option">skip-plugins: &lt;list&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			跳过加载所有或部分主题。
			<br />
			默认值：<code>&quot;&quot;</code>
		</td>
		<td>
			<code class="flag">--skip-themes[=&lt;theme&gt;]</code>
		</td>
		<td>
			<code class="option">skip-themes: &lt;list&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			跳过加载所有已安装的包。
			<br />
			默认值：<code>false</code>
		</td>
		<td>
			<code class="flag">--skip-packages</code>
		</td>
		<td>
			<code class="option">skip-packages: &lt;bool&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			在运行命令前加载 PHP 文件（可多次使用）。
			<br />
			默认值：<code>[]</code>
		</td>
		<td>
			<code class="flag">--require=&lt;path&gt;</code>
		</td>
		<td>
			<code class="option">require: &lt;path&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			在运行命令前执行 PHP 代码（可多次使用）。
			<br />
			默认值：<code>[]</code>
		</td>
		<td>
			<code class="flag">--exec=&lt;php-code&gt;</code>
		</td>
		<td>
			<code class="option">exec: &lt;php-code&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			在给定的上下文中加载 WordPress。
			<br />
			默认值：<code>auto</code>
		</td>
		<td>
			<code class="flag">--context[=&lt;context&gt;]</code>
		</td>
		<td>
			<code class="option">context: &lt;context&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			要禁用的（子）命令。
			<br />
			默认值：<code>[]</code>
		</td>
		<td>
			<em>不作为标志使用</em>
		</td>
		<td>
			<code class="option">disabled_commands: &lt;list&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			是否对输出进行着色。
			<br />
			默认值：<code>&quot;auto&quot;</code>
		</td>
		<td>
			<code class="flag">--[no-]color</code>
		</td>
		<td>
			<code class="option">color: &lt;bool&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			显示所有 PHP 错误；增加 WP-CLI 引导的详细程度。
			<br />
			默认值：<code>false</code>
		</td>
		<td>
			<code class="flag">--debug[=&lt;group&gt;]</code>
		</td>
		<td>
			<code class="option">debug: &lt;group&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集的值。
			<br />
			默认值：<code>false</code>
		</td>
		<td>
			<code class="flag">--prompt[=&lt;assoc&gt;]</code>
		</td>
		<td>
			<em>不作为选项使用</em>
		</td>
	</tr>
	<tr>
		<td>
			抑制信息性消息。
			<br />
			默认值：<code>false</code>
		</td>
		<td>
			<code class="flag">--quiet</code>
		</td>
		<td>
			<code class="option">quiet: &lt;bool&gt;</code>
		</td>
	</tr>
	<tr>
		<td>
			要报告为已加载的 Apache 模块列表。
			<br />
			默认值：<code>[]</code>
		</td>
		<td>
			<em>不作为标志使用</em>
		</td>
		<td>
			<code class="option">apache_modules: &lt;list&gt;</code>
		</td>
	</tr>
	</tbody>
</table>

## 配置文件

WP-CLI 可以自动发现并读取几种配置文件类型中的选项（当它们存在时）：

1. 当前工作目录（或上级目录）中的 `wp-cli.local.yml` 文件。
1. 当前工作目录（或上级目录）中的 `wp-cli.yml` 文件。
1. `~/.wp-cli/config.yml` 文件（路径可以通过设置 `WP_CLI_CONFIG_PATH` 环境变量来更改）。

除了上述全局参数外，配置文件还可以包含任何子命令的默认值，以及指向一个或多个 WordPress 安装的别名。

以下是一个带注释的 `wp-cli.yml` 文件示例：

	# 全局参数默认值
	path: wp-core
	url: http://example.com
	user: admin
	color: false
	disabled_commands:
	  - db drop
	  - plugin install
	require:
	  - path-to/command.php

	# 子命令默认值（例如 `wp config create`）
	config create:
		dbuser: root
		dbpass: 
		extra-php: |
			define( 'WP_DEBUG', true );
			define( 'WP_POST_REVISIONS', 50 );

	# 指向其他 WordPress 安装的别名（例如 `wp @staging rewrite flush`）
	# 别名可以包含 'user'、'url'、'path'、'ssh' 或 'http'
	@staging:
		ssh: wpcli@staging.wp-cli.org
		user: wpcli
		path: /srv/www/staging.wp-cli.org
	@production:
		ssh: wpcli@wp-cli.org:2222
		user: wpcli
		path: /srv/www/wp-cli.org

	# 别名可以引用其他别名以创建别名组
	# 别名组可以嵌套
	@both:
	 - @staging
	 - @production

	# '_' 是一个特殊值，表示此 wp-cli.yml 的配置选项
	_:
		# 合并来自上游 config.yml 的子命令默认值，而不是覆盖
		merge: true
		# 从任意 YAML 文件继承配置
		inherit: prod.yml

## Remote (SSH) configuration

Using the `ssh` option, WP-CLI can be configured to run on a remote system rather than the current system. Along with the SSH protocol, WP-CLI also supports connecting to Docker containers (including docker-compose) and Vagrant VMs.

The connection type can be passed via the scheme of the `--ssh` parameter or `ssh` option.

Supported types are:

* `docker:[<user>@]<container_id>` - Runs WP-CLI in a running Docker container via `docker exec [--user <user>] <container_id> ...`
* `docker-compose:[<user>@]<container_id>` - Runs WP-CLI in a running Docker container via `docker-compose exec [--user <user>] <container_id> ...`
* `docker-compose-run:[<user>@]<container_id>` - Runs WP-CLI in a new Docker container via `docker-compose run [--user <user>] <container_id> ...`
* `vagrant` - Runs WP-CLI in a running Vagrant VM via `vagrant ssh ...`
* `[<user>@]<host>[:<port>]` (ssh) - Runs WP-CLI on a remote machine through an SSH connection via `ssh [-p <port>] [<user>@]<host> ...`

All connection types support an optional `path` suffix to specify a directory to `cd` to before running WP-CLI; `path` is a full system path starting with either `/` or `~`. (If `WP_CLI_SSH_PRE_CMD` is specified, `cd` is run after this pre-command.)

The SSH connection type also supports two advanced connection configuration options, which must be specified via an alias in the YAML configuration:

* `proxyjump` - Specifies a jumpbox connection string, which is passed to `ssh -J`
* `key` - Specifies the key (identify file) to use, which is passed to `ssh -i`

See the documentation about [running WP-CLI commands remotely](https://make.wordpress.org/cli/handbook/guides/running-commands-remotely/) for more information.

## 上下文配置

在 WP-CLI v2.6.0 版本中，新增了一个全局标志 `--context=<context>`，允许用户选择 WP-CLI 执行命令时所处的 WordPress 上下文环境。

其主要目标之一是让 WP-CLI 能够更新高级插件和主题，而无需任何特殊设置。根据我们的初步测试，这使得大量流行的高级扩展在更新流程方面能够与 WP-CLI *直接兼容*™。

该标志的可能取值：

* `cli`：在此标志引入之前一直作为默认值的上下文环境。这是一种介于前端和管理请求之间的状态，旨在解决在控制台运行时 WordPress 的一些特殊问题。
* `admin`：模拟在管理后台执行命令的上下文环境。此选项旨在解决某些插件通过 `is_admin()` 检查来限制功能所导致的问题。
* `auto`：根据所使用的命令在 `cli` 和 `admin` 之间自动切换。目前，所有 `wp plugin *` 和 `wp theme *` 命令使用 `admin` 上下文，而所有其他命令使用 `cli` 上下文。
* `frontend`：[开发中] 此选项目前尚未生效。

在初始版本（v2.6.0）中，`--context` 标志默认设置为 `cli`。在 WP-CLI v2.7.0 及更高版本中，默认值已更改为 `auto`。这种渐进式部署允许主机服务商和网站所有者在默认行为更改之前，通过手动设置上下文来对 v2.6.0 版本进行测试。

如果您仍在使用 WP-CLI v2.6.0 但希望使用 `--context=auto` 的默认设置，可以通过在全局 `wp-cli.yml` 配置文件中添加必要的 `context: auto` 行来实现。如果您对此不熟悉，请随时查阅关于 [WP-CLI 配置文件](#config-files) 的文档。

## 环境变量

WP-CLI 的行为可以通过环境变量在运行时进行修改：

* `WP_CLI_CACHE_DIR` - 存储 WP-CLI 文件缓存的目录。默认为 `~/.wp-cli/cache/`。
* `WP_CLI_CONFIG_PATH` - 全局 `config.yml` 文件的路径。默认为 `~/.wp-cli/config.yml`。
* `WP_CLI_CUSTOM_SHELL` - 允许用户覆盖默认使用的 `/bin/bash` shell。
* `WP_CLI_DISABLE_AUTO_CHECK_UPDATE` - 禁用 WP-CLI 的自动更新检查。
* `WP_CLI_DOCKER_NO_TTY` - 忽略检测到的 tty 状态，并在通过 ssh 对 docker 容器运行 WP-CLI 时从 `docker exec` 命令中移除 `--tty` 标志。
* `WP_CLI_DOCKER_NO_INTERACTIVE` - 忽略检测到的 tty 状态，并在通过 ssh 对 docker 容器运行 WP-CLI 时从 `docker exec` 命令中移除 `--interactive` 标志。
* `WP_CLI_PACKAGES_DIR` - 存储通过 WP-CLI 包管理器安装的包的目录。默认为 `~/.wp-cli/packages/`。
* `WP_CLI_PHP` - 覆盖系统默认 PHP 二进制文件时使用的 PHP 二进制路径（仅适用于非 Phar 安装）。
* `WP_CLI_PHP_ARGS` - 调用 WP-CLI 时传递给 PHP 二进制文件的参数（仅适用于非 Phar 安装）。
* `WP_CLI_SSH_PRE_CMD` - 当使用 `--ssh=<ssh>` 时，在 WP-CLI 于远程服务器上调用 WP-CLI 之前执行一个命令。
* `WP_CLI_SSH_BINARY` - 当使用 `--ssh=<ssh>` 时，这是在远程机器上替代 `wp` 被调用的命令。
* `WP_CLI_STRICT_ARGS_MODE` - 通过告诉 WP-CLI 将命令前的任何参数视为全局参数，命令后的参数视为本地参数，来避免歧义。
* `WP_CLI_SUPPRESS_GLOBAL_PARAMS` - 设置为 `true` 以跳过在帮助屏幕末尾显示全局参数。这为高级用户节省了屏幕空间。
* `WP_CLI_FORCE_USER_LOGIN` - 设置为 `1` 以强制将提供给 `--user` 标志的值解释为登录名而非 ID，以解决类型歧义问题。
* `WP_CLI_EARLY_REQUIRE` - 在引导过程的早期加载一个或多个自定义 PHP 文件（逗号分隔）。
* `WP_CLI_REQUIRE` - 在引导过程之后加载一个或多个自定义 PHP 文件（逗号分隔）。这与命令行上的 `--require` 或 wp-cli.yml 配置文件中的 `require` 映射具有相同效果。
* `WP_CLI_USER_AGENT` - 设置某些插件和工具所依赖的 `$_SERVER['HTTP_USER_AGENT']` 值。

要按需设置环境变量，只需将环境变量定义放在要运行的 WP-CLI 命令之前。

    # 使用 vim 编辑文章
    $ EDITOR=vim wp post edit 1

要为每个 shell 会话设置相同的环境变量值，您需要将环境变量定义包含在您的 `~/.bashrc` 或 `~/.zshrc` 文件中。

    # 始终使用 vim 编辑文章
    export EDITOR=vim