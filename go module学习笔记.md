---
name: "go module学习笔记"
createdat: 2019-06-22
tags:
    - golang
    - go module
    - 依赖管理
---

## go module学习笔记
### 何为go module
一个module是一组包,这些包时以go.mod文件所在目录作为根目录的.

### module的作用是什么
module机制的提出是为了简化依赖管理.若是没有go module机制,就不得不逐个使用go get 去下载一个个依赖.
而有了go module后,就可以使用go的工具链完成包依赖的自动下载\更新与移除.

### 如何使用
#### 创建一个module
> 假设你想在trymodule文件夹下创建一个module名为iserver
```
cd trymodule
go mod init iserver
```
使用go mod init 会创建一个go.mod文件
> cat go.mod
```
module iserver

go 1.12
```
一个module只需要创建一个go.mod文件,也就是在项目的根目录下, 如果我们在根目录下又创建了一个新的目录hello,然后又在hello中写了一个hello包,那么这个包会自动被识别为iserver module的一部分

#### 添加一个依赖
当在包文件中引入了任意一个包后,使用go工具链中的go fmt/ go test等工具都会自动完成依赖的添加

#### 添加特定版本的依赖

#### 升级依赖

#### 升级依赖至特定版本

#### 移除不再使用的依赖

### 参考文章
