# Git Book插件

Git Book插件用于增强gitbook命令生成目标产物时能力。

## 插件使用方法

1.在[book.json](book.json.md)文件中添加配置项：

```json
{
  "plugins": [
    "expandable-chapters-small"
  ]
}
```

2.执行`gitbook install`本地安装插件包，其实际是node_modules模块。


## 默认带有的5个插件

| 名称          | 功能         |
|:--------------|:-------------|
| highlight     | 代码高亮      |
| search        | 导航栏搜索功能 |
| sharing       | 右上角分享功能 |
| font-settings | 字体设置面板  |
| livereload    | 暂时未知      |


## 常用插件

- expandable-chapters-small  
  支持左侧导航栏折叠，配合SUMMARY.md一起使用。

