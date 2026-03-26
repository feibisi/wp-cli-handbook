---
title: "自定义医生诊断检查"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Doctor
    - Guides
    - Repos
---

# 自定义医生诊断检查

尽管 `wp doctor` 自带[一系列默认诊断检查](https://make.wordpress.org/cli/handbook/doctor-default-checks/)，但其核心设计具备可扩展性。检查在运行时定义，通过读取 `doctor.yml` 配置文件来指定每个检查及其选项。

## doctor.yml 格式

让我们看看包含的 `doctor.yml` 文件中的前两项检查：

    autoload-options-size:
      check: Autoload_Options_Size
    constant-savequeries-falsy:
      check: Constant_Definition
      options:
        constant: SAVEQUERIES
        falsy: true

在这个例子中：

*   'autoload-options-size' 和 'constant-savequeries-falsy' 是检查的 _名称_。名称在所有已注册的检查中必须是唯一的。
*   `Autoload_Options_Size` 和 `Constant_Definition` 是 `runcommand\Doctor\Checks` 命名空间中的可重用检查类。你也可以使用它们，或者你可以编写自己的类继承 `runcommand\Doctor\Checks\Check` 并以 'class: yourNamespace\\yourClassName' 的形式提供。
*   'constant' 和 'falsy' 是 `Constant_Definition` 类接受的配置选项。在这个例子中，我们告诉 doctor 确保 `SAVEQUERIES` 为 false 或未定义。

为了完整性，也值得注意 `Autoload_Options_Size` 接受 'threshold\_kb' 作为一个可选的配置选项。'threshold\_kb' 的默认值是 900，因此不需要包含在 `doctor.yml` 中。

## 自定义 doctor.yml 配置文件

通过创建 `doctor.yml` 并使用 `wp doctor check --config=doctor.yml` 来运行您自己的医生检查。通过创建单独的 `prod.yml` 和 `dev.yml` 文件，为不同环境使用不同的配置。

如果您希望自定义文件扩展现有的医生配置，可以使用神奇的 `_` 配置文件选项来定义要继承的配置文件。'default' 是对捆绑的 `doctor.yml` 的神奇引用；您也可以指定完整的文件路径。

请看这个示例：

    _:
      inherit: default
      skipped_checks:
        - autoload-options-size
    constant-disallow-file-mods-falsy:
      check: Constant_Definition
      options:
        constant: DISALLOW_FILE_MODS
        falsy: true
    plugin-akismet-active
      check: Plugin_Status
      options:
        plugin: akismet
        status: active
    plugin-akismet-valid-api-key:
      class: Akismet_Valid_API_Key
      require: akismet-valid-api-key.php

这个自定义的 `doctor.yml` 文件：

*   继承了除 'autoload-options-size' 之外的所有默认诊断检查。
*   定义了一个 'constant-disallow-file-mods-falsy' 检查，以确保 `DISALLOW_FILE_MODS` 常量为假值。
*   定义了一个 'plugin-akismet-active' 检查，以确保 Akismet 处于激活状态。
*   定义了一个 'plugin-akismet-valid-api-key' [在 akismet-valid-api-key.php 文件中的自定义检查](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-write-custom-check/)，以确保 Akismet 拥有有效的 API 密钥。

## 可用检查类型

部分 `wp doctor` 检查类型是可配置的，意味着可以更改默认设置；而其他检查类型经过抽象化处理，使其可重复使用。例如，`Autoload_Options_Size` 检查接受 'threshold\_kb' 选项，而 `Plugin_Status` 接受 'plugin' 和 'status' 作为选项。

可配置的检查类型包括：

*   `check: Autoload_Options_Size`：接受 'threshold\_kb' 选项以设置阈值（单位：千字节）。默认值为 900。
*   `check: Cron_Count`：接受 'threshold\_count' 选项以设置定时任务总数阈值。默认值为 50。
*   `check: Cron_Duplicates`：接受 'threshold\_count' 选项以设置重复定时任务阈值。默认值为 10。
*   `check: Plugin_Active_Count`：接受 'threshold\_count' 选项以设置活动插件总数阈值。默认值为 80。
*   `check: Plugin_Deactivated`：接受 'threshold\_percentage' 选项以设置停用插件百分比阈值。默认值为 40。

抽象化的检查类型包括：

*   `check: Constant_Definition`：断言给定常量已定义、具有特定值或为假值。[了解更多](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-check-constant-value/)。
*   `check: File_Contents`：检查全部或部分 WordPress 文件是否符合给定正则表达式模式。[了解更多](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-check-file-contents/)。
*   `check: Option_Value`：断言给定选项具有特定值。[了解更多](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-check-option-value/)。
*   `check: Plugin_Status`：断言给定插件处于活动、已安装或未安装状态。[了解更多](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-check-plugin-status/)。

当然，部分检查类型不需要配置选项：

*   `check: Core_Update`：当有新的 WordPress 次要版本可用时报错；主要版本则警告。
*   `check: Core_Verify_Checksums`：根据发布的校验和验证 WordPress 文件；失败时报错。
*   `check: Plugin_Update`：当有插件更新可用时警告。
*   `check: Theme_Update`：当有主题更新可用时警告。

您可以通过扩展 `runcommand\Doctor\Checks\Check` 类来[编写自定义检查类型](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-write-custom-check/)。