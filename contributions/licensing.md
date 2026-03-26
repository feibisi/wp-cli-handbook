---
title: "许可协议"
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

# 许可协议

WP-CLI 采用 [MIT 许可证](https://github.com/wp-cli/wp-cli/blob/master/LICENSE)。本文档概述了 WP-CLI 对第三方代码的许可要求。

## 将第三方代码纳入官方仓库/组织

所有被纳入官方 [WP-CLI GitHub 组织](https://github.com/wp-cli) 下仓库的代码必须与 MIT 许可证兼容。这确保了 WP-CLI 可以继续被任何人自由使用、修改和分发。

## 捆绑第三方代码

当将第三方代码直接捆绑到 WP-CLI 包中时（即，将代码复制到仓库中，而不是声明为依赖项），该代码必须：

1. **采用与 MIT 兼容的许可证**
2. **包含原始许可证文件或头部信息** - 必须保留第三方代码的许可条款
3. **保留版权声明** - 原始版权声明必须保持完整
4. **明确标识** - 应清楚标明哪些代码是第三方代码及其来源

如果不确定是否应捆绑第三方代码，请考虑通过 Composer 将其作为依赖项使用。

## 依赖第三方代码

声明为依赖项的第三方包（通过 Composer 或其他包管理器）必须采用与 MIT 兼容的许可证。这适用于：

* **直接依赖项** - 在 `composer.json` 中明确列出的包
* **传递依赖项** - 依赖项的依赖项

### 检查依赖项许可证

在添加新依赖项之前：

1. 检查依赖项的 `LICENSE` 文件或 `composer.json` 中的许可证信息
2. 验证该依赖项的所有自身依赖项是否也兼容
3. 使用 `composer show -t` 查看包含许可证信息的依赖树，或安装 `composer/satis` 等额外工具来运行 `composer licenses` 进行详细的许可证审计

## 为什么有这些要求？

这些许可要求确保了：

1. **WP-CLI 保持自由和开放** - 用户可以无法律顾虑地使用、修改和分发 WP-CLI
2. **允许商业使用** - 公司可以在其产品中使用和集成 WP-CLI
3. **无许可证冲突** - WP-CLI 生态系统中的所有代码在法律上是兼容的
4. **用户使用简单** - 用户无需跟踪多个许可要求

## 有问题吗？

如果您对许可有疑问，或需要澄清特定许可证是否兼容，请提交 issue 或联系 [WP-CLI 维护者](https://github.com/orgs/wp-cli/teams/maintainers)。