---
title: "为 WP-CLI 编写 Behat 测试"
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

# 为 WP-CLI 编写 Behat 测试

WP-CLI 使用 [Behat](https://behat.org/) 进行功能测试。本指南将帮助您了解如何为 WP-CLI 命令和包编写并运行 Behat 测试。

## 简介

### 什么是 Behat 测试？

Behat 是一个面向 PHP 的行为驱动开发（BDD）框架。在 WP-CLI 中，Behat 测试被用作功能测试，用于执行完整命令并验证其是否按预期工作。与孤立测试单个函数的单元测试不同，功能测试确保命令能够端到端地正确运行。

### Behat 测试的重要性

WP-CLI 向用户承诺的重要契约是版本间的稳定性。Behat 测试有助于确保：

- 命令按文档所述正常工作
- 变更不会破坏现有功能
- 边界情况得到妥善处理
- 整个命令执行流程得到验证

**大多数拉取请求都需要测试。** 如果是新功能，需要测试。如果是修复错误，则需要测试以防止回归。

### 快速开始

每个包含命令的 WP-CLI 代码库都有一个 `features/` 目录，其中包含一个或多个 YAML 格式的 `*.feature` 文件。

## 编写你的第一个测试

### 基本测试结构

以下是一个简单示例：

```gherkin
Feature: 管理 WordPress 选项

  Scenario: 读取单个选项
    Given 一个 WordPress 安装

    When 我运行 `wp option get home`
    Then STDOUT 应为：
      """
      https://example.com
      """
```

此测试遵循 Gherkin 语法，包含三个关键组成部分：

- **`Feature:`** - 记录文件的范围。应描述被测试的整体功能。
- **`Scenario:`** - 描述一个具体的测试用例。每个功能文件可以包含多个场景。
- **Given** - 为测试设置初始环境（前置条件）。
- **When** - 触发一个事件发生（被测试的操作）。
- **Then** - 断言事件完成后预期的结果（验证）。

以更人性化的形式表述：

> 我有一个 WordPress 安装。当我运行 `wp option get home` 时，该命令的输出应为 'https://example.com'。

### 你的第一个测试

让我们为一个假设的显示问候语的命令编写测试：

1. 创建文件 `features/greeting.feature`：

```gherkin
Feature: 测试问候命令

  Scenario: 显示问候语
    Given 一个空目录

    When 我运行 `wp greeting hello`
    Then STDOUT 应包含：
      """
      Hello
      """
    And 返回码应为 0
```

这个测试：
1. 从一个空目录开始
2. 运行你的命令
3. 验证输出包含 "Hello"
4. 验证命令执行成功（退出码为 0）

### 常用步骤定义

WP-CLI 提供了许多预构建的步骤定义。以下是最常用的：

#### Given（前置条件）

- `Given an empty directory` - 创建一个干净的工作目录
- `Given a WP install` - 安装全新的 WordPress 实例
- `Given a WP multisite install` - 以多站点模式安装 WordPress
- `Given a database` - 创建一个空数据库

#### 何时（操作）

- `当运行 'wp command' 时` - 执行命令并期望成功
- `当尝试 'wp command' 时` - 执行命令（无论成功或失败）
- `当在后台启动 'wp command' 时` - 在后台运行命令

#### 然后（断言）

- `然后 STDOUT 应为：` - 输出完全匹配
- `然后 STDOUT 应包含：` - 输出包含文本
- `然后 STDOUT 不应包含：` - 输出不包含文本
- `然后返回码应为 0` - 命令执行成功
- `然后返回码应为 1` - 命令执行失败
- `然后 STDOUT 应为空` - 未产生输出

完整可用步骤列表请参阅 [Behat 步骤参考](https://make.wordpress.org/cli/handbook/references/behat-steps/)。

### 运行测试

#### 设置测试环境

运行测试前，你需要设置一个测试数据库。`composer behat` 脚本会自动检测数据库可用性，如果没有正在运行的数据库，则会回退到 SQLite，这使得无需任何设置即可轻松开始。

你有两个选择：

**选项 1：SQLite（推荐，简单）**

运行测试最简单的方法是使用 SQLite，它不需要数据库设置：

```bash
WP_CLI_TEST_DBTYPE=sqlite composer behat
```

或者直接运行 `composer behat`，如果没有配置数据库，它会自动使用 SQLite。

**选项 2：MySQL/MariaDB**

如果你更倾向于使用 MySQL 或 MariaDB，请运行设置脚本来创建测试数据库：

```bash
composer prepare-tests
```

这将创建一个 MySQL 用户 `wp_cli_test`，密码为 `password1`，该用户对 `wp_cli_test` 数据库拥有完全权限。

**注意：** MySQL 8.0 更改了默认的身份验证插件。如果你遇到连接问题，请参阅[这篇博客文章](https://jonathandesrosiers.com/2019/02/trouble-connecting-to-database-when-using-mysql-8-x/)以获取解决方案。

#### 运行测试套件

运行所有测试：

```bash
composer behat
```

运行特定功能文件的测试：

```bash
composer behat -- features/option.feature
```

运行特定场景（通过行号）：

```bash
composer behat -- features/option.feature:10
```

以详细输出模式运行：

```bash
composer behat -- features/option.feature --format pretty
```

仅重新运行失败的测试：

```bash
composer behat-rerun
```

#### 发现可用步骤

要查看所有可用的步骤定义：

```bash
composer behat -- --definitions l
```

这在编写测试时很有帮助，可以找到符合需求的正确步骤。

## 高级用法

### 编写有效的测试

#### 每次只测试一件事

每个场景应测试单一功能：

```gherkin
# 良好 - 测试一个特定行为
场景：删除文章
  假设一个 WP 安装
  并且我运行 `wp post create --post_title='Test' --porcelain`
  并且将 STDOUT 保存为 {POST_ID}

  当我运行 `wp post delete {POST_ID}`
  那么 STDOUT 应包含：
    """
    Success: Trashed post
    """

# 不佳 - 测试多个不相关的行为
场景：创建、更新和删除文章
  # 一个测试中内容过多...
```

#### 使用描述性的场景名称

明确说明测试内容：

```gherkin
# 良好示例
场景：当文章不存在时优雅地失败

# 不良示例
场景：测试删除
```

#### 同时测试成功与失败情况

不要只测试理想路径：

```gherkin
场景：成功创建文章
  假设一个 WP 安装
  当我运行 `wp post create --post_title='Test'`
  那么返回码应为 0

场景：缺少必要参数时失败
  假设一个 WP 安装
  当我尝试 `wp post create`
  那么返回码应为 1
  并且 STDERR 应包含：
    """
    错误
    """
```

### 使用变量

将命令输出存储在变量中供后续使用：

```gherkin
Scenario: 创建并获取文章
  Given 一个已安装的 WP

  When 我运行 `wp post create --post_title='Test Post' --porcelain`
  Then 将 STDOUT 保存为 {POST_ID}

  When 我运行 `wp post get {POST_ID} --field=title`
  Then STDOUT 应为：
    """
    Test Post
    """
```

### 测试表格和结构化输出

#### 测试表格输出

```gherkin
Scenario: 以表格格式列出文章
  Given 一个已安装的 WP
  And 我运行 `wp post create --post_title='First'`
  And 我运行 `wp post create --post_title='Second'`

  When 我运行 `wp post list --fields=ID,post_title`
  Then STDOUT 应该是一个包含以下行的表格：
    | ID | post_title |
    | 1  | First      |
    | 2  | Second     |
```

#### Testing JSON Output

```gherkin
Scenario: List posts in JSON format
  Given a WP install
  And I run `wp post create --post_title='Test' --porcelain`

  When I run `wp post list --format=json`
  Then STDOUT should be JSON containing:
    """
    [{"post_title":"Test"}]
    """
```

#### 测试 CSV 输出

```gherkin
Scenario: 将文章导出为 CSV
  Given 一个已安装的 WP
  
  When 我运行 `wp post list --format=csv`
  Then STDOUT 应为包含以下内容的 CSV：
    | ID | post_title | post_status |
    | 1  | Test       | publish     |
```

### 测试文件和目录

```gherkin
场景：创建一个插件文件
  假设有一个 WordPress 安装

  当我运行 `wp scaffold plugin my-plugin`
  那么 my-plugin/my-plugin.php 文件应该存在
  并且 my-plugin/my-plugin.php 文件应包含：
    """
    Plugin Name: My Plugin
    """
```

### 背景部分

使用 `Background:` 为所有场景执行通用设置：

```gherkin
Feature: 文章管理

  Background:
    Given 一个已安装的 WP
    And 我运行 `wp post create --post_title='Test'`

  Scenario: 更新文章标题
    When 我运行 `wp post update 1 --post_title='Updated'`
    Then STDOUT 应包含:
      """
      Success
      """

  Scenario: 删除文章
    When 我运行 `wp post delete 1`
    Then STDOUT 应包含:
      """
      Success
      """
```

### 测试错误信息

使用 `When I try` 替代 `When I run` 以允许命令执行失败：

```gherkin
Scenario: Error when plugin doesn't exist
  Given a WP install

  When I try `wp plugin activate non-existent-plugin`
  Then the return code should be 1
  And STDERR should contain:
    """
    Error: The 'non-existent-plugin' plugin could not be found.
    """
```

### 使用场景大纲

使用单一场景测试多个输入：

```gherkin
Scenario Outline: 使用不同标题创建文章
  Given 一个已安装的 WP

  When 我运行 `wp post create --post_title='<title>'`
  Then STDOUT 应包含：
    """
    Success
    """

  Examples:
    | title          |
    | Simple Title   |
    | Title's Quotes |
    | UTF-8: 日本語   |
```

### 编写自定义步骤

对于高级使用场景，您可能需要自定义步骤定义。这些定义在您软件包的测试引导文件中以 PHP 编写。

**自定义步骤定义示例：**

```php
/**
 * @Given a custom configuration file
 */
public function aCustomConfigurationFile() {
    $config = <<<EOT
custom_setting: value
another_setting: 123
EOT;
    $this->proc( "echo '{$config}' > wp-cli.yml" )->run_check();
}
```

自定义步骤应：
- 具有描述性的文档块注解
- 遵循 Gherkin 约定（Given/When/Then）
- 可在多个测试中重复使用
- 使用现有的 WP-CLI 测试框架方法

对于大多数软件包，[wp-cli/wp-cli-tests](https://github.com/wp-cli/wp-cli-tests) 中的内置步骤定义已足够。仅在必要时才创建自定义步骤。

### 在不同 PHP 和 WordPress 版本下进行测试

WP-CLI 测试在 CI 中针对多个 PHP 和 WordPress 版本运行。您的测试应能在这些版本中正常工作。

请注意：
- WordPress 的行为在不同版本间可能有所差异
- 使用适合版本的预期结果
- 避免测试 WordPress 核心错误（测试您的命令，而非 WordPress）

### 数据库凭据

默认情况下，MySQL/MariaDB 测试使用：
- 数据库：`wp_cli_test`
- 用户名：`wp_cli_test`
- 密码：`password1`
- 主机：`localhost`

可以通过 [wp-cli/wp-cli-tests](https://github.com/wp-cli/wp-cli-tests#the-database-credentials) 中的环境变量覆盖这些设置：

- `WP_CLI_TEST_DBNAME`
- `WP_CLI_TEST_DBUSER`
- `WP_CLI_TEST_DBPASS`
- `WP_CLI_TEST_DBHOST`

或者，通过设置 `WP_CLI_TEST_DBTYPE=sqlite` 使用 SQLite，从而完全避免数据库配置。

## 最佳实践

### 应该做的

- **测试命令行为，而非实现** - 测试应验证命令做了什么，而非如何做的
- **保持测试独立性** - 每个测试应能独立成功运行
- **使用有意义的测试数据** - 使用真实的帖子标题、用户名等
- **测试边界情况** - 空字符串、特殊字符、大数字
- **保持场景聚焦** - 每个场景只做一个逻辑测试
- **使用 Given 步骤进行设置** - 不要混合设置和测试
- **测试错误条件** - 验证命令是否按预期失败

### 注意事项

- **不要测试 WordPress 核心功能** - 测试你的命令，而非 WordPress
- **不要让测试相互依赖** - 每个场景都应独立运行
- **不要使用硬编码的 ID** - 使用变量或 porcelain 输出
- **不要跳过错误测试** - 失败命令的测试至关重要
- **不要测试实现细节** - 关注面向用户的行为
- **不要忘记测试帮助文本** - 包含 `wp help your-command` 的场景

## 为新包搭建测试框架

创建新的 WP-CLI 包时，使用 `wp scaffold package-tests` 命令生成测试基础设施：

```bash
wp scaffold package my-package
cd my-package
wp scaffold package-tests .
```

这将创建：
- `.github/workflows/testing.yml` - GitHub Actions 工作流文件
- `features/` - 功能测试文件目录
- `features/load-wp-cli.feature` - 验证 WP-CLI 加载的基础测试
- 其他测试基础设施文件

更多详情请参阅 [scaffold-package-command 文档](https://github.com/wp-cli/scaffold-package-command#wp-scaffold-package-tests)。

## 故障排除

### 测试无法连接数据库

如果出现数据库连接错误：

1. 尝试改用 SQLite：`WP_CLI_TEST_DBTYPE=sqlite composer behat`
2. 如果使用 MySQL，请确认其正在运行：`mysql -u wp_cli_test -ppassword1 wp_cli_test`
3. 检查你的 MySQL 版本（MySQL 8.0 有身份验证变更）
4. 确认数据库已创建：`composer prepare-tests`

### 本地测试通过但在 CI 中失败

常见原因：
- PHP 版本不同（检查你的 CI 矩阵配置）
- WordPress 版本不同（检查你的测试矩阵配置）
- 时序问题（某些命令需要更长时间才能完成）
- 数据库排序规则差异

### 命令未找到错误

如果在测试过程中命令未找到：

1. 确认您的 `composer.json` 已正确声明该命令
2. 检查 `composer install` 是否成功运行
3. 确保您的命令类已正确自动加载

### 慢速测试

如果测试运行缓慢：
- 尽量减少数据库操作
- 尽可能使用 `Given an empty directory` 而非 `Given a WP install`
- 避免不必要的插件安装
- 使用 `--porcelain` 来减少输出解析

## Additional Resources

- [Behat Steps Reference](https://make.wordpress.org/cli/handbook/references/behat-steps/) - Complete list of available steps
- [WP-CLI Test Framework](https://github.com/wp-cli/wp-cli-tests) - The underlying test framework
- [Behat Documentation](https://behat.org/en/latest/) - Official Behat documentation
- [Writing Functional Tests for WP-CLI Packages](https://deliciousbrains.com/writing-functional-tests-wp-cli-packages/) - Detailed tutorial
- [Pull Request Guidelines](https://make.wordpress.org/cli/handbook/contributions/pull-requests/) - Contributing guidelines

## WP-CLI 包中的示例

来自 WP-CLI 核心包的真实示例：

- [核心命令测试](https://github.com/wp-cli/core-command/tree/main/features) - 测试安装和更新的示例
- [搜索替换命令测试](https://github.com/wp-cli/search-replace-command/tree/main/features) - 测试数据库操作
- [脚手架命令测试](https://github.com/wp-cli/scaffold-command/tree/main/features) - 测试文件生成

研究这些示例，了解在实践中如何测试不同类型的命令。