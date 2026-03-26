---
title: "编写用于断言给定选项值的检查"
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

# 编写用于断言给定选项值的检查

`wp doctor` 中包含的检查类型之一是 `Option_Value`，即断言给定选项为特定值的能力。该检查类型已被多个[默认诊断检查](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-default-checks/)使用，你也可以在[自定义的 `doctor.yml` 配置文件](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-customize-config/)中使用 `Option_Value` 检查类型。

例如，以下是两个使用 `Option_Value` 的检查，一个确保博客是公开的，另一个确保用户无法注册：

    option-blog-public:
      check: Option_Value
      options:
        option: blog_public
        value: 1
    option-users-can-register:
      check: Option_Value
      options:
        option: users_can_register
        value: 0

一起运行时，你可能会看到：

    $ wp doctor check --config=option-value.yml --all
    +---------------------------+---------+-------------------------------------------------+
    | name                      | status  | message                                         |
    +---------------------------+---------+-------------------------------------------------+
    | option-blog-public        | error   | Site is private but expected to be public.      |
    | option-users-can-register | success | Option 'users_can_register' is '0' as expected. |
    +---------------------------+---------+-------------------------------------------------+

`Option_Value` 检查类型接受以下选项：

* 'option': 选项的名称。
* 'value': 选项预期为的特定值。