---
title: "编写用于断言给定常量值的检查"
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

# 编写用于断言给定常量值的检查

`wp doctor` 中包含的检查类型之一是 `Constant_Definition`，即能够断言给定常量是否已定义、是否为特定值或是否为假值。该检查类型已被多个[默认诊断检查](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-default-checks/)使用，你也可以在[自定义的 `doctor.yml` 配置文件](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-customize-config/)中使用 `Constant_Definition` 检查类型。例如，以下是两个使用 `Constant_Definition` 的检查，一个确保 `SAVEQUERIES` 未定义，另一个确保 `DISALLOW_FILE_MODS` 为 true：

    constant-savequeries-falsy:
      check: Constant_Definition
      options:
        constant: SAVEQUERIES
        falsy: true
    constant-disallow-file-mods-true:
      check: Constant_Definition
      options:
        constant: DISALLOW_FILE_MODS
        value: true

一起运行时，你可能会看到：

    $ wp doctor check --config=constant-definition.yml --all
    +----------------------------------+---------+--------------------------------------------------+
    | name                             | status  | message                                          |
    +----------------------------------+---------+--------------------------------------------------+
    | constant-savequeries-falsy       | success | Constant 'SAVEQUERIES' is undefined.             |
    | constant-disallow-file-mods-true | success | Constant 'DISALLOW_FILE_MODS' is defined 'true'. |
    +----------------------------------+---------+--------------------------------------------------+

`Constant_Definition` 检查类型接受以下选项：

* 'constant': 常量名称。
* 'defined': 期望常量已定义。
* 'value': 期望常量是特定值。
* 'falsy': 期望常量未定义或为假值。