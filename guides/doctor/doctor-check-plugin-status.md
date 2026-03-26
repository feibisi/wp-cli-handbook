---
title: "检查指定插件的状态"
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

# 检查指定插件的状态

`wp doctor` 包含的检查类型之一是 `Plugin_Status`，即能够断言指定插件应处于激活、已安装或未安装状态。虽然该检查类型未被任何[默认诊断检查](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-default-checks/)使用，但您可以在[自定义的 `doctor.yml` 配置文件](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-customize-config/)中使用 `Plugin_Status` 检查类型。

例如，以下是两个使用 `Plugin_Status` 的检查示例：一个确保 Akismet 在系统中处于激活状态，另一个确保 Hello Dolly 处于未安装状态：

    plugin-akismet-active:
      check: Plugin_Status
      options:
        name: akismet
        status: active
    plugin-hello-uninstalled:
      check: Plugin_Status
      options:
        name: hello
        status: uninstalled

同时运行时，您可能会看到：

    $ wp doctor check --config=plugin-status.yml --all
    +--------------------------+---------+----------------------------------------------------------------+
    | name                     | status  | message                                                        |
    +--------------------------+---------+----------------------------------------------------------------+
    | plugin-akismet-active    | success | Plugin 'akismet' is 'active' as expected.                      |
    | plugin-hello-uninstalled | error   | Plugin 'hello' is 'inactive' but expected to be 'uninstalled'. |
    +--------------------------+---------+----------------------------------------------------------------+

`Plugin_Status` 检查类型接受以下选项：

* 'name'：插件名称，与 `wp plugin list` 中显示的名称一致。
* 'status'：期望的插件状态，可选值为 'active'、'installed' 或 'uninstalled'。