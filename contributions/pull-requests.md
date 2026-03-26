---
title: "拉取请求"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Contributions
    - Repos
    - Data
---

# 拉取请求

WP-CLI 采用拉取请求工作流程来处理代码（和文档）的变更。无论您是想修复错误还是实现新功能，流程基本一致：

0. [搜索现有议题](https://github.com/search?q=org%3Awp-cli+is%3Aopen+sort%3Aupdated-desc&type=issues)；如果找不到与您想处理内容相关的议题，请在适当的仓库中新建一个议题，以便获得初步反馈。
    1. 在提交拉取请求前先开一个议题，有助于我们在您花费太多时间编写代码之前，提供架构和实现方面的指导。
1. 复刻您想要修改的仓库，可以是框架或某个命令包。
    1. 有关为开发配置代码库的更多详情，请参阅[设置](#setting-up)。
2. 为您要处理的每个议题创建一个分支。提交您的更改。
3. 将代码更改从本地克隆推送到您的复刻仓库。
4. 打开一个拉取请求。代码是否完美并不重要，关键在于尽早获得审查并在此基础上迭代。
5. 及时响应[代码审查反馈](https://make.wordpress.org/cli/handbook/code-review/)，认识到开发是一个协作过程。
6. 一旦您的拉取请求通过代码审查，它将被合并到默认分支，并进入下一个版本的发布流程。

不熟悉 WP-CLI 命令？您可能想[从命令手册开始](https://make.wordpress.org/cli/handbook/commands-cookbook/)，了解更多关于命令如何工作的信息。

您可能想要编辑的仓库分为三类：

* [wp-cli/wp-cli](https://github.com/wp-cli/wp-cli/) 是框架实现。
* [wp-cli/scaffold-command](https://github.com/wp-cli/scaffold-command/) 是命令实现的一个示例。还有很多其他命令仓库。
* [wp-cli/handbook](https://github.com/wp-cli/handbook/) 包含手册中呈现的文档。

## 期望

提交拉取请求时，请牢记以下几点期望。

**测试是必需的**

大多数情况下，我们会要求添加功能测试或单元测试来覆盖变更。如果是新功能，拉取请求需要包含测试。如果是修复错误，拉取请求也需要包含测试。

有关编写和运行测试的更多信息，请参阅下面的文档。

**遵循 WordPress 编码标准**

虽然尚未严格执行，但 WP-CLI 项目通常遵循 [WordPress 编码标准](http://make.wordpress.org/core/handbook/coding-standards/)。如果您的拉取请求偏离标准太多，我们可能会要求您进行清理。

**请避免不必要的代码改动**

不应仅仅因为能够重构就进行代码重构。对于一个存在多年的代码库，有无数的最佳实践、可读性或一致性改进可以进行。然而，进行任何此类改动都会带来不明显的成本：我们的时间和注意力、使 Git 历史更难以审查等。任何代码更改都应具有明确且明显的价值。

**贡献应是原子性的**

为了使您的代码更容易合并，每个拉取请求应仅包含一个概念上的更改。保持贡献的原子性可以使拉取请求的讨论集中在一个主题上，并使得能够逐个案例地批准更改。

如果您提交的拉取请求包含多个概念上的更改，我们将要求您重新提交为单独的拉取请求。

**在您的贡献上保持定期进展**

通过[我们的代码审查流程](https://make.wordpress.org/cli/handbook/code-review/)，我们将与您合作，确保您的拉取请求已准备好合并。但如果需要更改，并且我们在**两周内**没有收到您的回复，我们将认为该拉取请求已被放弃。其他人可能会接手并进行所需的更改。或者它可能会被关闭。

如果您因任何原因需要离开，请在拉取请求或相关问题上发表评论，以便我们可以在需要时接手或暂停处理。

## 环境配置

如果您之前从未提交过拉取请求，您需要安装 WP-CLI 进行本地开发。根据您希望处理特定命令/包还是整个项目的不同，具体流程略有差异。

### 处理特定命令/包

1. 若未安装 [Composer](https://getcomposer.org/)，请先安装。
2. 将需要处理的命令/包的 git 仓库克隆到本地。以处理 `wp core` 命令为例：`git clone https://github.com/wp-cli/core-command.git`
3. 进入克隆的目录：`cd core-command`
4. 安装所有 Composer 依赖项：`composer install`
5. 验证 WP-CLI 是否已正确安装：`vendor/bin/wp --info`

在此包中，建议优先使用 `vendor/bin/wp` 来运行命令。直接使用 `wp` 通常也可行，但那样可能会通过不同版本的框架运行命令，从而得到意外结果。

### 整体项目开发

1. 如果尚未安装，请先安装 [Composer](https://getcomposer.org/)。
2. 将 WP-CLI git 仓库克隆到本地机器：`git clone git@github.com:wp-cli/wp-cli.git ~/wp-cli`
3. 进入克隆的目录：`cd ~/wp-cli`。如果你要开发核心框架本身，请通过 GitHub 网页界面 [fork 该仓库](https://docs.github.com/en/get-started/quickstart/fork-a-repo) 并 [将其添加为远程仓库](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#adding-a-remote-repository)：`git remote add fork git@github.com:yourusername/wp-cli.git`
4. 安装所有 Composer 依赖项：`composer install --prefer-source`
5. 将 `wp` 命令别名指向新的 WP-CLI 安装：`alias wp='~/wp-cli/bin/wp'`
6. 验证 WP-CLI 是否安装正确：`wp --info`

WP-CLI 捆绑的命令（例如 `wp scaffold plugin`）可以在 `vendor/wp-cli` 目录（例如 `vendor/wp-cli/scaffold-command`）中进行编辑。安装 WP-CLI 时使用 `--prefer-source` 标志可确保每个命令都以 Git 克隆方式安装，便于提交更改。

可独立安装的命令（例如 `wp dist-archive`）可以从源代码安装（例如 `wp package install git@github.com:wp-cli/dist-archive-command.git`）。运行 `wp package path <package-name>` 可找到要编辑的相应目录。

重要的是，你需要 fork 每个仓库才能拥有可推送的远程仓库。对于每个你想贡献的仓库：

1. 通过 GitHub 网页界面 [fork 该仓库](https://docs.github.com/en/get-started/quickstart/fork-a-repo)
2. [将你的 fork 添加为远程仓库](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#adding-a-remote-repository)：

    $ cd vendor/wp-cli/scaffold-command
    $ git remote add fork git@github.com:yourusername/scaffold-command.git
    $ git remote -v
    origin  https://github.com/wp-cli/scaffold-command.git (fetch)
    origin  https://github.com/wp-cli/scaffold-command.git (push)
    fork    git@github.com:yourusername/scaffold-command.git (fetch)
    fork    git@github.com:yourusername/scaffold-command.git (push)

完成这些步骤后，你的 GitHub 账户中将拥有一个 fork 仓库和一个可以推送的新远程仓库。然后，你可以使用 `git push fork branch-name` 将更改推送到你的 fork。

**可选：** [GitHub CLI (`gh`)](https://cli.github.com/) 可以帮助简化其中一些任务，例如从命令行 fork 仓库和创建拉取请求。

## 运行和编写测试

自动化测试分为三种类型：

* 代码风格检查器，使用 [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer) 实现
* 功能测试，使用 [Behat](http://behat.org) 实现
* 单元测试，使用 [PHPUnit](http://phpunit.de/) 实现

### 代码风格检查器

代码风格检查器确保代码遵循指定的编码规范，避免就空格或对齐等次要细节进行不必要的讨论。

它们还会检查已知的错误来源和 PHP 兼容性问题。

运行检查：

    composer phpcs

自动修复可修复的错误和警告：

    vendor/bin/phpcbf

### 功能测试

WP-CLI 使用 [Behat](https://behat.org/) 进行功能测试。功能测试通过端到端执行命令来确保它们按预期工作。

关于编写和运行 Behat 测试的完整指南，请参阅 **[编写 Behat 测试](https://make.wordpress.org/cli/handbook/guides/behat-tests/)**。

以下是一个 Behat 测试的简单示例：

```yml
Feature: 管理 WordPress 选项

  Scenario: 读取单个选项
    Given 一个 WP 安装

	When 我运行 `wp option get home`
	Then STDOUT 应该是:
      """
	  https://example.com
	  """
```

在这个示例中：

- `Feature:` 描述文件的范围。
- `Scenario:` 描述一个具体的测试。
- `Given` 提供测试的初始环境。
- `When` 触发一个事件。
- `Then` 断言事件完成后预期的结果。

#### 创建测试数据库

运行功能测试前，您需要一个名为 `wp_cli_test` 的 MySQL（或 MariaDB）用户，密码为 `password1`，并对 MySQL 数据库 `wp_cli_test` 拥有完全权限。
如需覆盖这些凭据，可使用 [wp-cli-tests 的数据库凭据常量](https://github.com/wp-cli/wp-cli-tests#the-database-credentials)。

如果用户具备正确权限，也可通过运行 `composer prepare-tests` 来设置数据库。这将创建数据库和用户并配置必要权限。注意此操作无需每次测试都运行，仅在首次初始化设置时需要执行。

**注意：若使用 MySQL >= 8.0，可能会遇到 WP-CLI 成功连接数据库时的不一致问题。MySQL 8.0 更改了默认身份验证插件，部分客户端（如 PHP）尚未支持此变更。更多信息可参阅[此博客文章](https://jonathandesrosiers.com/2019/02/trouble-connecting-to-database-when-using-mysql-8-x/)。**

#### 运行测试套件

然后，运行整个测试套件：

    composer behat

或者测试特定行的场景：

    composer behat -- features/core.feature:10

或者测试单个功能：

    composer behat -- features/core.feature

或者以更详细的方式测试单个功能：

    composer behat -- features/core.feature --format pretty

仅运行上次运行中失败的测试：

    composer behat-rerun

编写新测试时，查看可用的步骤定义：

    composer behat -- --definitions l

更多信息可通过 `composer behat -- --help` 获取。

### Unit tests

The unit test files are in the `tests/` directory.

To run the unit tests, execute:

    composer phpunit

To run a specific unit test, you can use:

    composer phpunit -- filter=<method name>

### 一次性运行所有测试

要一次性运行所有测试：

    composer test

这将根据相应配置文件的存在情况，运行该软件包设置使用的所有测试。

每个代码仓库都配置为在每次代码推送时运行其所有活跃测试。[wp-cli/automated-tests](https://github.com/wp-cli/automated-tests) 仓库会定期运行所有仓库的所有测试。

## 最后...

感谢！开发 WP-CLI 应该是有趣的。如果您发现任何难以理解的地方，请告诉我们，以便改进流程或文档！