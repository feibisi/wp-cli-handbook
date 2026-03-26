---
title: "WP-CLI 常用任务"
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

# WP-CLI 常用任务

不确定 WP-CLI 能做什么？本页面展示了您可以通过命令行完成的实用日常 WordPress 管理任务，并提供了可立即使用的示例。

> **命令行新手？** 请先阅读[入门指南](https://make.wordpress.org/cli/handbook/guides/beginners-guide/)。

## 插件

### 安装插件

```
wp plugin install contact-form-7
```

### 一步安装并激活插件

```
wp plugin install contact-form-7 --activate
```

### 激活已安装的插件

```
wp plugin activate contact-form-7
```

### 停用插件

```
wp plugin deactivate contact-form-7
```

### 更新特定插件

```
wp plugin update akismet
```

### 一次性更新所有插件

```
wp plugin update --all
```

### 列出所有已安装插件及其状态

```
wp plugin list
```

### 删除插件

```
wp plugin delete hello
```

## 主题

### 安装主题

```
wp theme install twentytwentyfour
```

### 激活主题

```
wp theme activate twentytwentyfour
```

### 更新所有主题

```
wp theme update --all
```

### 列出所有已安装的主题

```
wp theme list
```

## WordPress 核心

### 检查已安装的 WordPress 版本

```
wp core version
```

### 检查 WordPress 是否有可用更新

```
wp core check-update
```

### 将 WordPress 更新至最新版本

```
wp core update
```

### 更新 WordPress 数据库

```
wp core update-db
```

## 用户

### 列出所有用户

```
wp user list
```

### 创建新用户

```
wp user create jane jane@example.com --role=editor
```

### 修改用户密码

```
wp user update jane --user_pass=newpassword
```

### 删除用户

```
wp user delete jane --reassign=1
```

> **提示：** `--reassign=1` 选项会将已删除用户的文章转移到 ID 为 1 的用户（通常是网站管理员）名下。请将 `1` 替换为你希望接收文章的用户 ID。

### 为现有用户添加管理员角色

```
wp user set-role jane administrator
```

## 文章与页面

### 创建新文章

```
wp post create --post_title="My First Post" --post_status=publish --post_type=post
```

### 创建新页面

```
wp post create --post_title="About Us" --post_status=publish --post_type=page
```

### 列出所有已发布的文章

```
wp post list --post_status=publish
```

### 删除文章（将其移至回收站）

```
wp post delete 42
```

### 永久删除文章

```
wp post delete 42 --force
```

## 评论

### 列出所有待审核的评论

```
wp comment list --status=hold
```

### 批准一条评论

```
wp comment approve 5
```

### 删除垃圾评论

```
wp comment delete $(wp comment list --status=spam --format=ids)
```

> **注意：** `$(...)` 语法在 bash（macOS、Linux、Git Bash 或 Windows 上的 WSL）中有效。它在 Windows 命令提示符中无效。Windows 用户应使用 Git Bash、WSL 或 PowerShell 来运行此命令。

## 选项与设置

### 获取站点 URL

```
wp option get siteurl
```

### 获取站点标题

```
wp option get blogname
```

### 修改站点标题

```
wp option update blogname "我的新站点标题"
```

### 阻止搜索引擎收录网站

```
wp option update blog_public 0
```

### 重新启用搜索引擎收录

```
wp option update blog_public 1
```

## 搜索与替换

### 预览将站点迁移至新域名时的变更内容

```
wp search-replace 'http://oldsite.com' 'http://newsite.com' --dry-run
```

### 更换域名时替换 URL

```
wp search-replace 'http://oldsite.com' 'http://newsite.com'
```

## 媒体

### 重新生成所有缩略图尺寸

在更换主题或添加新图片尺寸后非常有用：

```
wp media regenerate --yes
```

## 缓存

### 刷新对象缓存

```
wp cache flush
```

### 刷新重写规则（在添加新插件或更改固定链接设置后很有用）

```
wp rewrite flush
```

## 数据库

### 将数据库导出到文件

```
wp db export backup.sql
```

### 从文件导入数据库

```
wp db import backup.sql
```

### 打开交互式数据库控制台

```
wp db cli
```

## WP-CLI 本身

### 检查已安装的 WP-CLI 版本

```
wp cli version
```

### 更新 WP-CLI 至最新版本

```
wp cli update
```

### 获取有助于故障排除的系统信息

```
wp --info
```

## 深入探索

这些示例仅触及皮毛。WP-CLI 几乎涵盖了 WordPress 的每个部分。要了解更多：

- 浏览[内置命令完整列表](https://developer.wordpress.org/cli/commands/)。
- 阅读[快速入门指南](https://make.wordpress.org/cli/handbook/guides/quick-start/)获取详细教程。
- 查看[外部资源](https://make.wordpress.org/cli/handbook/guides/external-resources/)获取教程、博客文章和视频。