# Git Book配置文件

在SUMMARY.md和README.md同级目录下，创建名为book.json的配置文件，该文件会被gitbook读取。

文件格式`json`，样例`book.json`如下。

```json
{
  "language": "zh-hans",
  "description": "This is such a great book!",
  "title": "Weber学习指南",
  "plugins": [
    "anchor-navigation-ex",
    "expandable-chapters",
    "splitter",
    "edit-link",
    "prism",
    "prism-themes",
    "-highlight",
    "search-plus",
    "-lunr",
    "-search",
    "advanced-emoji"
  ],
  "pluginsConfig": {
    "prism": {
      "css": [
        "prism-themes/themes/prism-xonokai.css"
      ]
    },
    "anchor-navigation-ex": {
      "showLevel": false,
      "mode": "float",
      "float": {
        "showLevelIcon": false,
        "level1Icon": "fa fa-hand-o-right",
        "level2Icon": "fa fa-hand-o-right",
        "level3Icon": "fa fa-hand-o-right"
      }
    },
    "edit-link": {
      "base": "https://github.com/lixinyao0722/my-book/blob/master",
      "label": "编辑本页"
    }
  }
}
```

| 字段        | 说明                                                |
|:------------|:----------------------------------------------------|
| author      | 作者                                                |
| language    | 生成语言，默认en，zh-hans为简体中文                    |
| gitbook     | 检查gitbook版本是否满足要求                           |
| description | 定义了书本的描述，默认是从 README（第一段）中提取的      |
| title       | 生成静态html时网站的title，会显示在chrome的tab标签页上  |
| plugins     | 应用插件列表。如：expandable-chapters支持左侧导航栏折叠 |

