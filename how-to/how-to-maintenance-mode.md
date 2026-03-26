---
title: "如何将网站置于维护模式"
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

# 如何将网站置于维护模式

WP-CLI 提供了启用、禁用维护模式以及检查维护模式是否启用的命令。

### 步骤 1 - 检查状态

```
    $ wp maintenance-mode status
    维护模式未激活。
```

### 步骤 2 - 启用维护模式

```
    $ wp maintenance-mode activate
    正在启用维护模式...
    成功：已激活维护模式。
```

### 步骤 3 - 禁用维护模式

```
    $ wp maintenance-mode deactivate
    正在禁用维护模式...
    成功：已停用维护模式。
```