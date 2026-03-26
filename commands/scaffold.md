---
title: "wp scaffold"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Commands
    - Repos
    - Data
---

# wp scaffold

为文章类型、分类法、插件、子主题等生成代码。

### 示例

    # 生成一个包含单元测试的新插件。
    $ wp scaffold plugin sample-plugin
    成功：已创建插件文件。
    成功：已创建测试文件。

    # 基于 _s 生成主题。
    $ wp scaffold _s sample-theme --theme_name="Sample Theme" --author="John Doe"
    成功：已创建主题 'Sample Theme'。

    # 在指定主题中生成文章类型注册代码。
    $ wp scaffold post-type movie --label=Movie --theme=simple-life
    成功：已创建 '/var/www/example.com/public_html/wp-content/themes/simple-life/post-types/movie.php'。