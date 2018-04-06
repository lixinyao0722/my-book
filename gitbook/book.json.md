# Git Book配置文件

在SUMMARY.md和README.md同级目录下，创建名为book.json的配置文件，该文件会被gitbook读取。

文件格式`json`，常用配置项如下。

```json
{
  "author": "lixinyao",
  "language": "zh-hans",
  "gitbook": ">=2.0.0",
  "description": "This is such a great book!",
  "title": "Weber学习指南",
  "plugins": [
    "expandable-chapters-small"
  ]
}
```

>- author：作者。
>- language：生成语言，默认en，zh-hans为简体中文。
>- gitbook：检查gitbook版本是否满足要求。
>- description：定义了书本的描述，默认是从 README（第一段）中提取的。
>- title：生成静态html时网站的title，会显示在chrome的tab标签页上。
>- plugins：应用插件列表。如：expandable-chapters-small支持左侧导航栏折叠。

