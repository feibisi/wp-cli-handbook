---
title: "wp media"
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

# wp media

将文件导入为附件、重新生成缩略图，或列出已注册的图片尺寸。

### 示例

    # 重新生成所有缩略图，无需确认。
    $ wp media regenerate --yes
    找到 3 张需要重新生成的图片。
    1/3 已为 "悉尼海港大桥" (ID 760) 重新生成缩略图。
    2/3 已为 "海滨木板路" (ID 757) 重新生成缩略图。
    3/3 已为 "河上旭日" (ID 756) 重新生成缩略图。
    成功：已重新生成 3 张图片中的 3 张。

    # 导入本地图片并将其设置为文章的精选图片。
    $ wp media import ~/Downloads/image.png --post_id=123 --title="一张下载的图片" --featured_image
    已将文件 '/home/person/Downloads/image.png' 作为附件 ID 1753 导入，并作为精选图片附加到文章 123。
    成功：已导入 1 张图片中的 1 张。

    # 列出所有已注册的图片尺寸
    $ wp media image-size
    +---------------------------+-------+--------+-------+
    | 名称                      | 宽度  | 高度   | 裁剪  |
    +---------------------------+-------+--------+-------+
    | full                      |       |        | N/A   |
    | twentyfourteen-full-width | 1038  | 576    | hard  |
    | large                     | 1024  | 1024   | soft  |
    | medium_large              | 768   | 0      | soft  |
    | medium                    | 300   | 300    | soft  |
    | thumbnail                 | 150   | 150    | hard  |
    +---------------------------+-------+--------+-------+

    # 修正特定图片的方向。
    $ wp media fix-orientation 63
    1/1 正在修正 "Portrait_6" (ID 63) 的方向。
    成功：已修正 1 张图片中的 1 张。