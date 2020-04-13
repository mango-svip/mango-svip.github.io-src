---
title: Go下载依赖比较慢的解决方法
date: 2020-04-07 14:02:08
comments: false
---

## 设置Go proxy 来解决下载依赖慢的问题
<!--more-->
打开你的终端并执行

```
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
完成
```

## macOS或Linux
```
$ export GO111MODULE=on
$ export GOPROXY=https://goproxy.cn
```

## Windows
```
打开 PowerShell 并执行
C:\> $env:GO111MODULE = "on"
C:\> $env:GOPROXY = "https://goproxy.cn"
```

---

## 自托管Go的模块代理

你的代码永远只属于你自己，因此我们向你提供目前世界上最炫酷的自托管 Go 模块代理搭建方案。通过使用 Goproxy 这个极简主义项目，你可以在现有的任意 Web 服务中轻松地加入 Go 模块代理支持，要知道 goproxy.cn 就是基于它搭建的。  

创建一个名为 goproxy.go 的文件  

```golang
package main

import (
	"net/http"
	"os"

	"github.com/goproxy/goproxy"
)

func main() {
	g := goproxy.New()
	g.GoBinEnv = append(
		os.Environ(),
		"GOPROXY=https://goproxy.cn,direct", // 使用 goproxy.cn 作为上游代理
		"GOPRIVATE=git.example.com",         // 解决私有模块的拉取问题（比如可以配置成公司内部的代码源）
	)
	http.ListenAndServe("localhost:8080", g)
}

```
并运行它  

然后通过把 GOPROXY 设置为 http://localhost:8080 来试用它。另外，我们也建议你把 GO111MODULE 设置为 on。  
就这么简单，一个功能完备的 Go 模块代理就搭建成功了。事实上，你可以将 Goproxy 结合着你钟爱的 Web 框架一起使用，比如 Gin 和 Echo，你所需要做的只是多添加一条路由而已。更高级的用法请查看[文档](https://pkg.go.dev/github.com/goproxy/goproxy)。  
