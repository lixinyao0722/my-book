# 解决gitbook编译命令错误

## 问题描述

使用`gitbook serve .`或`gitbook build . dist`编译命令时，经常出现如下错误。

![gitbook-cli-compile-bug](../assets/imgs/gitbook-cli-compile-bug.png)

## 解决方法

修改文件`copyPluginAssets.js`

![gitbook-cli-compile-bug-fix-mine](../assets/imgs/gitbook-cli-compile-bug-fix-mine.png)

![gitbook-cli-compile-bug-fix-code](../assets/imgs/gitbook-cli-compile-bug-fix-code.png)


## 参考

- [gitbook/issues/1309](https://github.com/GitbookIO/gitbook/issues/1309)

![gitbook-cli-compile-bug-solution](../assets/imgs/gitbook-cli-compile-bug-solution.png)
