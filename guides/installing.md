---
title: "安装"
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

# 安装

## 系统要求

WP-CLI 需要 **PHP 7.2.24 或更高版本**。要检查系统上可用的 PHP 版本，请运行：

```
php --version
```

除了 WordPress 本身的要求外，WP-CLI 没有其他额外要求。

## 推荐安装方式

推荐通过下载 Phar 构建文件（类似 Java JAR 文件的归档格式，[详见此文](http://php.net/manual/en/phar.using.intro.php)）来安装 WP-CLI，将其标记为可执行文件并放置于 PATH 环境变量中。

首先，使用 `wget` 或 `curl` 下载 [wp-cli.phar](https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar)。例如：

```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
```

### 验证下载文件（可选但推荐）

在使用下载的文件之前，您可以验证其真实性和完整性。请参阅我们的 [WP-CLI 下载验证指南](https://make.wordpress.org/cli/handbook/guides/verifying-downloads/)，了解如何使用 GPG 签名或校验和来确保文件未被篡改的详细说明。

使用 GPG 快速验证：

```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar.asc
curl -L https://raw.githubusercontent.com/wp-cli/builds/gh-pages/wp-cli.pgp | gpg --import
gpg --verify wp-cli.phar.asc wp-cli.phar
```

然后，检查它是否正常工作：

```
php wp-cli.phar --info
```

为了能够只输入 `wp` 而不是 `php wp-cli.phar`，您需要使文件可执行并将其移动到 PATH 中的某个位置。例如：

```
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```

现在尝试运行 `wp --info`。如果 WP-CLI 安装成功，您将看到类似以下的输出：

```
OS:  Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64
Shell:   /usr/bin/zsh
PHP binary:    /usr/bin/php
PHP version:     7.1.12-1+ubuntu16.04.1+deb.sury.org+1
php.ini used:   /etc/php/7.1/cli/php.ini
MySQL binary:
MySQL version:
SQL modes:
WP-CLI root dir:        /home/wp-cli/.wp-cli
WP-CLI packages dir:    /home/wp-cli/.wp-cli/packages/
WP-CLI global config:   /home/wp-cli/.wp-cli/config.yml
WP-CLI project config:
WP-CLI version: 1.5.0
```

恭喜！您现在正式成为 WP-CLI 用户。

想知道接下来该做什么？请查看 [快速入门指南](https://make.wordpress.org/cli/handbook/quick-start/)，获取简短介绍和一些使用示例。

### 更新 WP-CLI

如果您使用推荐的 Phar 方法安装了 WP-CLI，可以随时通过运行 `wp cli update` 来更新（但如果 WP-CLI 由 root 用户所有，可能需要使用 `sudo wp cli update`）。如果您使用 Composer 或基于 Git 的安装方式安装了 WP-CLI，请参阅下文每种方法对应的具体更新说明。

运行 `wp cli update` 时，系统会提示您确认是否要更新，显示类似以下信息：

```
当前版本为 0.21.1。是否要更新到 0.23.1？[y/n]
```

确认后，您将看到成功消息：

```
成功：WP-CLI 已更新至 0.23.1
```

如果您已运行最新版本的 WP-CLI，将看到以下消息：

```
WP-CLI 已是最新版本。
```

想体验前沿版本？运行 `wp cli update --nightly` 即可使用最新的 WP-CLI 夜间构建版。夜间构建版在本地环境中基本稳定可用，且始终包含最新最强大的功能。

有关 `wp cli update` 的更多信息（包括可用的标志和选项），请阅读完整的[更新命令文档页](https://developer.wordpress.org/cli/commands/cli/update/)。

### Tab 自动补全

#### Bash 与 Z-Shell

WP-CLI 为 _Bash_ 和 _Z-Shell_ 提供了自动补全脚本。只需下载 [wp-completion.bash](https://github.com/wp-cli/wp-cli/raw/main/utils/wp-completion.bash) 并在 `~/.bash_profile` 中引入：

```
source /完整路径/wp-completion.bash
```

要使更改在当前激活的 shell 中生效，请随后运行 `source ~/.bash_profile`。

#### Oh My Zsh

如果你正在使用 _Oh My Zsh_ 框架，你可以启用[内置的 `wp-cli` 插件](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/wp-cli)，只需将其添加到 `~/.zshrc` 文件中的 `plugins=(wp-cli git [...])` 这一行。

注意：Oh My Zsh 插件已包含 bash 自动补全脚本，因此无需同时启用两者。

要使此更改在当前活动的 shell 中生效，之后请运行 `source ~/.zshrc`。

#### Fish

如果你正在使用 _Fish_ shell，可以下载 [wp.fish](https://github.com/wp-cli/wp-cli/raw/main/utils/wp.fish) 并移动到 `~/.config/fish/completions/wp.fish`。
之后只需输入 `wp` 并按下 `TAB` 键，fish 将自动加载 `wp.fish`。

### Dash/Alfred 工作流

如果您正在使用 _Dash_ 和 _Alfred_，可以添加一个自定义的 Alfred 工作流来查找 WP-CLI 命令信息。

#### 设置

打开 Dash 并下载 [WP-CLI 文档集](https://github.com/wp-cli/dash-docset-generator)：
Dash › 偏好设置 › 下载 › 用户贡献 › 搜索 WP-CLI

仍在 Dash 中，激活 Alfred 集成：
Dash › 偏好设置 › 集成 › Alfred

#### 使用方法

打开 Alfred 并尝试搜索特定命令。例如，输入 `wp-cli plugin` 可查看 `plugin` 命令及其子命令的概览。

## 其他安装方式

**注意：** 对于以下所有基于 Phar 的安装方法，您都可以验证下载文件的真实性和完整性。具体操作说明请参阅 [WP-CLI 下载验证指南](https://make.wordpress.org/cli/handbook/guides/verifying-downloads/)。

### 通过 Git 安装

如果你打算参与 WP-CLI 的开发，请查阅 [Pull Requests](https://make.wordpress.org/cli/handbook/pull-requests/) 中的 [环境设置](https://make.wordpress.org/cli/handbook/pull-requests/#setting-up) 部分。

### 通过 Phar 安装夜间版

"夜间版"是 WP-CLI 的前沿版本，直接基于[主分支](https://github.com/wp-cli/wp-cli/commits/main)构建。

只需遵循常规的[安装说明](/#install)，但将 Phar 文件的 URL 更改为：

<https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli-nightly.phar>

### 通过 Composer 安装

**作为项目的一部分**

在项目的 `composer.json` 文件中添加以下行：

    "require" : {
    	"wp-cli/wp-cli-bundle": "*"
    }

要添加 `wp-cli-bundle` 包中看到的任何其他建议包（例如 `psy/psysh`），请运行：

```
composer require --dev $(composer suggests --by-package | awk '/wp-cli\/wp-cli-bundle/' RS= | grep -o -P '(?<=- ).*(?=:)')
```

可选地（如果在服务器上运行或在本地虚拟机中运行），您可以自动设置命令并使其在用户路径中可用。假设 _Composer_ 安装在 `/var/www/vendor` 目录下（您可以通过 `composer config --list | grep "\[vendor-dir\]"` 获取特定于您机器的 composer `vendor-dir` 配置变量），我们可以将以下 `scripts`/命令添加到 `composer.json` 文件中。第二行和第三行设置 [bash 自动补全](https://github.com/wp-cli/wp-cli/blob/main/utils/wp-completion.bash)，这样我们就不必记住每一个命令：

    "scripts" : {
    	"post-install-cmd" : [
    		"[[ -f /usr/bin/wp ]] || sudo ln -s /var/www/vendor/wp-cli/wp-cli/bin/wp /usr/bin/wp",
    		"source /var/www/vendor/wp-cli/wp-cli/utils/wp-completion.bash",
        "[[ -f ~/.bash_profile ]] || touch ~/.bash_profile",
    		"source ~/.bash_profile"
    	]
    }

上述脚本假设您当前的 shell 是 `bash`，但并非所有用户都是这种情况。以 vagrant 虚拟机为例（添加到 `scripts` 块中）：

    cat /etc/passwd | grep $(whoami)
    vagrant:x:1000:1000::/home/vagrant:/bin/bash

如果您的操作系统已安装并可用 `bash`，您可以动态切换：

    "scripts" : {
    	"post-update-cmd" : [
    		"/bin/bash -c \"[[ -f /usr/local/bin/wp ]] || sudo ln -s /var/www/vendor/wp-cli/wp-cli/bin/wp /usr/bin/wp\"",
    		"/bin/bash -c \"source /var/www/vendor/wp-cli/wp-cli/utils/wp-completion.bash\"",
        "/bin/bash -c \"[[ -f ~/.bash_profile ]] || touch ~/.bash_profile\"",
    		"/bin/bash -c \"source ~/.bash_profile\""
    	]
    }

**作为一个项目**

需要将 `php` 和 `composer`（或 `php composer.phar`）设置为控制台命令。

    composer create-project wp-cli/wp-cli-bundle --prefer-source

然后运行 `wp-cli-bundle/vendor/wp-cli/wp-cli/bin/wp`，或将 `wp-cli-bundle/vendor/wp-cli/wp-cli/bin` 文件夹添加到 `PATH` 中以使用全局 `wp` 命令（在 Windows 上，请使用 `wp-cli/bin/wp.bat`）。

要更新，您需要：

    cd wp-cli-bundle
    git pull origin main
    composer install

**全局安装**

如果您更喜欢通过 Composer 全局安装 PHP 工具，并且您的 PATH 中包含类似 `~/.composer/vendor/bin` 的路径（在 Windows 上是 `C:\Users\you\AppData\Roaming\Composer\vendor\bin`），您可以直接运行：

    composer global require wp-cli/wp-cli-bundle

要全局更新所有内容，请运行 `composer global update`。

**安装特定版本**

如果您想安装特定版本的 WP-CLI，请在包名后附加版本号。

composer create-project wp-cli/wp-cli-bundle:2.1.0 --no-dev

版本号必须采用 Composer 能够理解的[格式](https://getcomposer.org/doc/04-schema.md#version)，并且可以在 [packagist.org](https://packagist.org/packages/wp-cli/wp-cli) 上找到。

**安装前沿版本**

如果你想安装前沿版本，请使用 `dev-main`：

    composer create-project wp-cli/wp-cli-bundle:dev-main --no-dev

#### 作为项目全局安装

您可以为 WP-CLI 指定自定义安装路径，如下所示：

    composer create-project wp-cli/wp-cli-bundle /usr/share/wp-cli --no-dev

然后，只需创建二进制文件的符号链接：

    sudo ln -s /usr/share/wp-cli-bundle/vendor/wp-cli/wp-cli/bin /usr/bin/wp

### 通过 Homebrew 安装

    brew install wp-cli

这是 [formula](https://github.com/Homebrew/homebrew-core/blob/master/Formula/w/wp-cli.rb)。

### 通过 Docker 安装

Docker 社区维护着 [WordPress 和 WP-CLI 镜像](https://hub.docker.com/_/wordpress/)。

要在你自己的项目中包含 WP-CLI 镜像：

    image: wordpress:cli

### 在 Windows 上安装

通过 [上文所述的 composer 方式](#installing-via-composer) 安装，或使用以下方法。

确保已安装 php 并将其 [添加到系统路径](http://php.net/manual/en/faq.installation.php#faq.installation.addtopath)，以便全局执行。

手动下载 [wp-cli.phar](https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar) 并保存到文件夹，例如 `c:\wp-cli`

在 `c:\wp-cli` 中创建名为 `wp.bat` 的文件，内容如下：

    @ECHO OFF
    php "c:/wp-cli/wp-cli.phar" %*

将 `c:\wp-cli` 添加到系统路径：

    setx path "%path%;c:\wp-cli"

现在即可在 Windows 命令行的任意位置使用 WP-CLI。

### 通过 .deb 包安装

在 Debian 或 Ubuntu 上，只需下载并打开一个 .deb 包：<https://github.com/wp-cli/builds/tree/gh-pages/deb>

### 在 Fedora 30+ 上安装

    su -c 'dnf install wp-cli'

### 在 CentOS 上安装

    su -c 'yum install wp-cli'

### 使用自定义 PHP 二进制文件

在某些情况下，例如 MAMP 安装，您可能不希望使用默认的 PHP 二进制文件。

要使用 MAMP 提供的最新 PHP 版本，您需要修改 `PATH` 环境变量，将以下内容添加到您的 `~/.bash_profile` 或 `~/.zsh_profile` 中：

    PHP_VERSION=$(ls /Applications/MAMP/bin/php/ | sort -n | tail -1)
    export PATH=/Applications/MAMP/bin/php/${PHP_VERSION}/bin:$PATH

要使用 MAMP 提供的特定 PHP 版本，您需要确定该 PHP 版本可执行文件的路径，并修改 `PATH` 环境变量，将以下内容添加到您的 `~/.bash_profile` 或 `~/.zsh_profile` 中：

    export PATH=/Applications/MAMP/bin/php/php5.5.26/bin:$PATH

请注意，在这种情况下没有对 `PHP_VERSION` 变量进行赋值，因为我们不是动态查找最新的 PHP 版本。

添加并保存文件后，使用以下命令重新加载文件：

    source ~/.bash_profile

完成此操作后，运行 `wp --info` 以确保更改已正确应用。

对于基于 Composer 和 Git 的 WP-CLI 安装，如果您出于某种原因不想修改 `PATH`，也可以设置 `WP_CLI_PHP` 环境变量。

### 在 MediaTemple 上安装

请参阅 [http://razorfrog.com/installing-wp-cli-on-mediatemple-grid-server/](http://razorfrog.com/installing-wp-cli-on-mediatemple-grid-server/)