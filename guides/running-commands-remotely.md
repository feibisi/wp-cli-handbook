---
title: "远程运行命令"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Guides
    - Repos
    - Data
---

# 远程运行命令

## 使用 SSH 连接

WP-CLI 接受 `--ssh=[<scheme>:][<user>@]<host>[:<port>][<path>]` 全局参数，用于在远程 WordPress 安装上运行命令。该参数的用法类似于 `scp` 或 `git` 等工具中 SSH 连接的参数化方式。

在底层，WP-CLI 将命令代理到 ssh 可执行文件，然后由 ssh 将这些命令传递给远程机器上安装的 WP-CLI。`--ssh=[<scheme>:][<user>@]<host>[:<port>][<path>]` 的语法根据以下规则解析：

* **scheme** 参数默认为 `ssh`，也可接受 `vagrant`、`docker` 和 `docker-compose` 选项。
* 如果仅提供 **host**（例如 `wp --ssh=example.com`），则用户将推断为当前系统用户，端口为默认 SSH 端口（22），路径为 SSH 用户的主目录。
* 可以通过添加以 @ 符号结尾的前缀来覆盖 **user**（例如 `wp --ssh=admin_user@example.com`）。
* 可以通过添加以冒号开头的前缀来覆盖 **port**（例如 `wp --ssh=example.com:2222`）。
* 可以通过添加后缀来覆盖 **path**（例如 `wp --ssh=example.com~/webapps/production`）。路径紧接在端口之后，如果未显式设置端口，则紧接在主机顶级域名之后。
* 也可以提供存储在 `~/.ssh/config` 中的已知 **alias**（例如，对于 `@rc` 别名，使用 `wp --ssh=rc`）。

**注意：您需要在远程服务器上安装 WP-CLI 副本，且可通过 `wp` 命令访问。**

此外，如果您定义了 shell 别名或扩展了 `$PATH` 环境变量，`--ssh=<host>` 将不会加载您的 `~/.bash_profile`。如果这对您有影响，[这里有一个更详细的解释](https://make.wordpress.org/cli/handbook/running-commands-remotely/#making-wp-cli-accessible-on-a-remote-server)，说明如何使 `wp` 可访问。

### 方案

您可利用 ssh 参数的 scheme 组件，为连接本地容器化或虚拟化机器定义简写方式。

**scheme** 参数默认设为 `ssh`，但也接受 `vagrant`、`docker` 和 `docker-compose` 作为备选方案。

#### docker

使用 Docker 时，命令为：`wp rewrite flush --ssh=docker:<name>`
可通过 `docker ps` 命令查找 Docker 容器的名称。

#### docker-compose

对于 Docker Compose，命令为：`wp option get home_url --ssh=docker-compose:<name>`
可在 `docker-compose.yml` 文件中找到 Docker 容器的名称。

#### vagrant

使用 Vagrant 时，你可以使用命令：`wp rewrite flush --ssh=vagrant:<name>`

## 别名

WP-CLI 别名是你在 `wp-cli.yml` 或 `config.yml` 中注册的快捷方式，可以轻松地对任何 WordPress 安装运行命令。

例如，当你在本地工作，注册了一个新的重写规则，并且需要在基于 Vagrant 的虚拟机中刷新重写规则时，你可以运行：

```
# 在开发环境上运行刷新命令
$ wp @dev rewrite flush
成功：重写规则已刷新。
```

然后，当代码部署到生产环境后，你可以运行：

```
# 在生产环境上运行刷新命令
$ wp @prod rewrite flush
成功：重写规则已刷新。
```

你无需 SSH 进入机器、切换目录，通常也无需花费整整一分钟来访问特定的 WordPress 安装，你只需告诉 WP-CLI 要操作哪台机器，它就知道如何建立实际连接。

它还可以轻松利用 Vagrant 的 ssh 辅助命令来确定 SSH 参数，通过使用 `vagrant` 方案（如 `--ssh=vagrant:default`，其中 `default` 是 Vagrant 机器名称/ID）将 WP-CLI 命令通过管道传递给 `vagrant ssh`，或者如果像下面的示例一样定义为别名。一些 Vagrant 盒子[默认提供此功能](https://github.com/Chassis/Chassis/tree/main)，因此你可以直接在主机上使用 WP-CLI。

此外，别名组允许你注册别名组。如果你想对两个配置的示例站点运行命令，可以使用像 `@both` 这样的组：

```
# 在两个环境上运行更新检查
$ wp @both core check-update
成功：WordPress 已是最新版本。
成功：WordPress 已是最新版本。
```

别名可以在项目的 `wp-cli.yml` 文件或用户的全局 `~/.wp-cli/config.yml` 文件中注册：

```yaml
@prod:
  ssh: dev_user@example.com~/webapps/production
@dev:
  ssh: vagrant@192.168.50.10/srv/www/example.dev
@local:
  ssh: vagrant:default
@both:
  - @prod
  - @dev
```

你可以在[配置部分](https://make.wordpress.org/cli/handbook/config/#config-files)找到有关如何设置配置文件的更多信息。

## Running custom commands remotely

If you want to run a custom command on a remote server, that custom command needs to be installed on the remote server, but it does not have to be installed on the local machine you're launching `wp` from.

You can use the WP-CLI package manager remotely to install custom commands to remote machines.

Example:

```
# The command is not installed on either local or remote machine
$ wp db ack
Error: 'ack' is not a registered subcommand of 'db'. See 'wp help db'.
$ wp @dev db ack
Error: 'ack' is not a registered subcommand of 'db'. See 'wp help db'.

# To make the command work on the remote machine, we can install it remotely
# through the WP-CLI package manager
$ wp @dev package install runcommand/db-ack
Installing package runcommand/db-ack (dev-master)
Updating /home/vagrant/.wp-cli/packages/composer.json to require the package...
Using Composer to install the package...
---
Loading composer repositories with package information
Updating dependencies
Resolving dependencies through SAT
Dependency resolution completed in 0.311 seconds
Analyzed 4726 packages to resolve dependencies
Analyzed 162199 rules to resolve dependencies
Package operations: 1 install, 0 updates, 0 removals
Installs: runcommand/db-ack:dev-master aff8ccc
 - Installing runcommand/db-ack (dev-master aff8ccc)
Writing lock file
Generating autoload files
---
Success: Package installed.

# Now we can run the command remotely, even though it is not installed locally
$ wp @dev db ack test_email@example.com
wp_users:user_email
9:test_email@example.com
```

### 在 Windows Powershell 中运行

Windows Powershell 对 `@` 符号有特殊含义，这意味着不进行引号包裹或转义就无法使用它。
要远程运行命令，你需要使用以下表示法之一。

```sh
$ wp `@dev core version
$ wp "@dev" core version
```

## 在远程服务器上使 WP-CLI 可访问

通过 SSH 远程运行命令需要在远程服务器的 `$PATH` 中可访问 `wp`。由于 SSH 连接不会加载 `~/.bashrc` 或 `~/.zshrc`，使用 `wp --ssh=<host>` 时可能需要指定自定义的 `$PATH`。使 `wp` 在远程服务器上可用的几种方法包括：

### 将 WP-CLI 二进制文件复制到 $HOME/bin 目录

在许多 Linux 发行版中，`$HOME/bin` 默认已包含在 `$PATH` 环境变量中。因此，一种让 `wp` 命令可用的方法是：如果 `$HOME/bin` 目录不存在则创建它，然后将 WP-CLI 二进制文件移动到 `$HOME/bin/wp`：

```sh
mkdir -p ~/bin
cd ~/bin
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
mv wp-cli.phar wp
```

如果 `$HOME/bin` 尚未包含在您的路径中，可以在 `~/.bashrc` 文件（或远程服务器对应 shell 的等效配置文件）中定义：

```sh
#.bashrc
PATH="$HOME/bin:$PATH"
```

### 在 $HOME/.ssh/environment 中指定 $PATH

另一种实现方式是在远程机器用户的 `~/.ssh/environment` 文件中指定 `$PATH`，前提是该机器的 `sshd` 已配置 `PermitUserEnvironment=yes`（参见 [OpenSSH 文档](https://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#.7E.2F.ssh.2Fenvironment)）。

### 远程非交互式 Shell 解析别名并以别名方式运行 wp 与 php

某些虚拟主机配置限制非常严格：
- 不允许执行自定义 shell 脚本，因此[WP-CLI 二进制文件方法](#copy-wp-cli-binary-to-home-bin)完全失效。
- `sshd` 配置为 `PermitUserEnvironment=no`，导致自定义[~/.ssh/environment](#specify-the-path-in-home-ssh-environment) 无效且同样失败。
- 即使[在客户端使用 before_ssh 钩子](#using-before_ssh-hook-on-client-machine)也无济于事，因为所有情况下都无法在远程主机运行 `wp`。

解决方案：在远程主机按如下方式配置 `~/.bashrc`：

#### 配置远程非交互式 Shell 以解析别名

- 默认情况下，[非交互式 Shell 中的别名不会被解析](https://unix.stackexchange.com/questions/425319/how-do-i-execute-a-remote-alias-over-an-ssh/425323#425323)，但你可以更改此设置：
  - 在你的 `~/.bashrc` 文件的最顶部（务必在第一个别名定义之前）插入：

    ```
    shopt -s expand_aliases
    ```
  - 同时确保没有机制过早退出非交互式 Shell！如果顶部有如下结构（例如 Ubuntu 默认配置），请注释掉或删除该结构的所有行：
    ```
    # 如果不是交互式运行，则不执行任何操作
    [ -z "$PS1" ] && return
    ```

#### 将 wp 别名指向运行 WP-CLI 二进制文件的 php 命令

- 在 `shopt -s expand_aliases` 行之后的某处插入：
  - `alias wp="php ~/bin/wp"`
  - 或
  - `alias wp="php ~/bin/wp-cli.phar"`
- 换言之：您创建了一个别名 "wp"，它是一行命令，其中 php 通过指定 `wp-cli.phar` 文件的路径来运行 WP-CLI 二进制文件，无论该文件位于何处或使用何种名称。
  - `php` 基本上在任何网络主机上都可用。
  - 而 `wp-cli.phar` 文件本身甚至无需设置执行标志（="可以完全被动"），因为从形式上讲，该文件是由 `php` 运行（=解释）的。**注意：** 一个可执行的 `~/bin/wp` 文件（重命名后的 `wp-cli.phar` 并设置了执行标志）最终当然也会由 `php` 解释器运行。但在 shell 中的调用形式上是不同的。而这正是此处关键的区别所在。

### 在客户端使用 before_ssh 钩子

或者，如果您无法在服务器端使其正常工作，可以通过挂载 `before_ssh` 钩子并定义一个包含您要运行的命令的环境变量来实现相同的效果：

```php
WP_CLI::add_hook( 'before_ssh', function() {

    $host = WP_CLI\Utils\parse_ssh_url(
        WP_CLI::get_runner()->config['ssh'],
        PHP_URL_HOST
    );

    switch( $host ) {
        case 'example.com':
            putenv( 'WP_CLI_SSH_PRE_CMD=export PATH=$HOME/bin:$PATH' );
            break;
    }
} );
```

如果您将上述代码放入 `pre-ssh.php` 文件中，可以通过在 `~/.wp-cli/config.yml` 文件中引入该文件，从而为整个环境加载它：

```yaml
require:
  - pre-ssh.php
```