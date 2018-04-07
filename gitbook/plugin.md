# Git Book插件

Git Book插件用于增强gitbook命令生成目标产物时能力。

## 插件使用方法

1.在[book.json](book.json.md)文件中添加配置项。若插件有额外配置，可另添加pluginsConfig。

```json
{
  "plugins": [
    "expandable-chapters",
    "anchor-navigation-ex"
   ],
  "pluginsConfig": {
    "anchor-navigation-ex": {
      "showLevel": false,
      "mode": "float",
      "float": {
        "showLevelIcon": false,
        "level1Icon": "fa fa-hand-o-right",
        "level2Icon": "fa fa-hand-o-right",
        "level3Icon": "fa fa-hand-o-right"
      }
    }
  }
}
```

2.安装插件包，其实际是node_modules模块，两种方式如下。

```bash
gitbook install
npm i gitbook-plugin-expandable-chapters --save
```


## 默认带有的5个插件

| 名称          | 功能         |
|:--------------|:-------------|
| highlight     | 代码高亮      |
| search        | 导航栏搜索功能 |
| sharing       | 右上角分享功能 |
| font-settings | 字体设置面板  |
| livereload    | 暂时未知      |

如果需要取消默认插件，方式如下。

```json
{
  "plugins": [
    "-font-settings"
  ]
 }
```

## 常用插件

### book.json

```json
{
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

- expandable-chapters  
  支持左侧导航栏折叠，配合SUMMARY.md一起使用。
- anchor-navigation-ex  
  添加Toc到侧边悬浮导航以及回到顶部按钮，配置参数点击
  [此处](https://github.com/zq99299/gitbook-plugin-anchor-navigation-ex/blob/master/doc/config.md)。
- splitter  
  使侧边栏的宽度可以自由调节
- edit-link  
  页面顶部出现编辑当前页面按钮
- prism  
  取代gitbook默认提供的代码高亮功能，使用方法如下。

```json
{
  "plugins": [
    "prism",
    "prism-themes",
    "-highlight"
  ]
}
```

- search-plus  
  左侧导航栏上的搜索框，支持全局模糊搜索中文，使用方法。

```json
{
  "plugins": [
    "search-plus",
    "-lunr",
    "-search"
  ]
}
```

- advanced-emoji  
  支持emoji图标，使用方式如`:kissing_heart:`:kissing_heart:，更多图标大全请点击
  [此处](https://www.webpagefx.com/tools/emoji-cheat-sheet/) 。

## 参考

- https://www.npmjs.com/package/gitbook-plugin-toc
- [GitBook 插件](http://gitbook.zhangjikai.com/plugins.html)
- https://zq99299.gitbooks.io/gitbook-guide/content/chapter/plugin.html
