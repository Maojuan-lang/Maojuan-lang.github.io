---
title: golang
date: 2024-07-30
---

```
初始化go.mod：
go mod init 项目名称
整理依赖：
go mod tidy
代理：
go env -w GOPROXY="https://goproxy.cn,direct"
-w参数代表修改后面变量的值，不带-w仅为查看变量的值
```

```
下载GO插件支持golang语言，下载gopls包进行代码提示，设置gopls的环境变量启动
GOPATH：是开发的工作目录。用于保存编译后的二进制文件。go get命令和go install命令会下载go的代码到GOPATH中。
使用GOPATH时，项目中import引用的第三方包，首先会从GOROOT/src下搜索，如果搜索不到，会到GOPATH/src目录下搜索。
```

