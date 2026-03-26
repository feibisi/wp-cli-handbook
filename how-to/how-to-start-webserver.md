---
title: "如何启动 Web 服务器"
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

# 如何启动 Web 服务器

您可以使用 `wp server` 命令来启动 PHP 的内置 Web 服务器，用于特定的 WordPress 安装。默认情况下，Web 服务器将使用 localhost 和默认端口 8080 启动，但您可以使用 `--host` 和 `--port` 选项来更改它们。

### 步骤 1 - 使用默认设置启动 Web 服务器

```
    $ wp server
    PHP 7.2.24-0ubuntu0.18.04.4 Development Server started at Thu Jun  4 17:40:13 2020
    Listening on http://localhost:8080
    Document root is ../wpdemo.test
    Press Ctrl-C to quit.
```

上面的命令使用默认设置启动了服务器。现在我们可以打开浏览器并访问链接 http://localhost:8080 来访问我们的 WordPress 安装。

### 步骤 2 - 使用不同设置启动 Web 服务器

如果您想指定不同的端口号或主机，可以将它们传递给以下标志：
`--port` 和 `--host`

```
    $ wp server --port=9090 --host=192.168.0.4
```

上面的命令将启动 Web 服务器并在 http://192.168.0.4:9090 上监听请求，您可以打开浏览器并访问该页面来访问您的 WordPress 安装。