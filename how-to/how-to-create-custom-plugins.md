---
title: "如何创建自定义插件"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - How To
    - Repos
    - Data
---

# 如何创建自定义插件

如果您想创建自己的插件，WP-CLI 提供了一个强大的脚手架命令，允许我们生成起始代码。在本指南中，我们将了解如何为基本插件生成起始代码。

## 步骤 1 - 创建插件文件脚手架

以下命令使用多个选项，让我们可以指定插件别名、名称、描述、作者姓名和 URI 以及插件 URI。您可以根据需要替换传递给以下选项的值来自定义插件。

```
    $ wp scaffold plugin wpcli-demo-plugin --plugin_name="WP-CLI Demo Plugin" --plugin_description="This is a wp-cli demo plugin" --plugin_author=wp-cli --plugin_author_uri="https://wp-cli.org" --plugin_uri="https://plugins.wp-cli.org/demo-plugin"
    Success: Created test files.
```

上述命令在插件目录中生成一个名为 `wpcli-demo-plugin` 的新文件夹，具有以下文件结构。

    | - bin/
    | - tests/
    | - .gitignore
    | - .editorconfig
    | - .phpcs.xml.dist
    | - .travis.yml
    | - Gruntfile.js
    | - package.json
    | - phpunit.xml.dist
    | - readme.txt
    | - wpcli-demo-plugin.php

除非使用 --skip-tests 标志，否则始终会生成以下文件：

- `phpunit.xml.dist` 是 PHPUnit 的配置文件。
- `.travis.yml` 是 Travis CI 的配置文件。使用 `--ci=<provider>` 选择不同的服务。
- `bin/install-wp-tests.sh` 配置 WordPress 测试套件和测试数据库。
- `tests/bootstrap.php` 是在运行测试套件时激活当前插件的文件。
- `tests/test-sample.php` 是包含测试用例的示例文件。
- `.phpcs.xml.dist` 是 PHP_CodeSniffer 规则的集合。

## 步骤 2 - 创建自定义文章类型：

现在我们可以再次使用脚手架命令，通过 `wp scaffold post-type` 命令在我们的新插件中添加一个自定义文章类型。

```
    $ wp scaffold post-type books --label=Book --textdomain=wpcli-demo-plugin --dashicon=dashicons-book-alt --plugin=wpcli-demo-plugin
    Success: Created '/wpcli-demo-plugin/post-types/books.php'.
```

## 步骤 3 - 在主文件中编写代码：

主插件文件 `wpcli-demo-plugin.php` 是我们编写插件逻辑的起点。

现在，让我们在主插件文件中引用刚刚创建的新文章类型。

在你喜欢的文本编辑器中打开文件 `wpcli-demo-plugin.php`，
在写着“你的代码从这里开始”的那一行下面添加以下内容：

```
\\你的代码从这里开始。
require('post-types/books.php');
```

## 步骤 4 - 激活插件

现在你可以使用两个 wp-cli 命令来检查插件列表并激活你新创建的插件。
`wp plugin list` 和 `wp plugin activate`。第一个命令列出所有已安装的插件，而第二个命令则激活指定的插件。

```
    $ wp plugin list
    +-------------------+----------+-----------+---------+
    | name              | status   | update    | version |
    +-------------------+----------+-----------+---------+
    | akismet           | inactive | available | 4.1.5   |
    | hello             | inactive | none      | 1.7.2   |
    | wpcli-demo-plugin | inactive | none      | 0.1.0   |
    +-------------------+----------+-----------+---------+
```

从上面的列表中我们可以看到我们的插件 wpcli-demo-plugin 处于未激活状态。让我们使用另一个命令来启用它。

```
    $ wp plugin activate wpcli-demo-plugin
    Plugin 'wpcli-demo-plugin' activated.
    Success: Activated 1 of 1 plugins.
```

我们的插件现在已经激活。我们可以访问 WordPress 管理面板并开始使用我们的书籍自定义文章类型。