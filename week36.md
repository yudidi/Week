# Algorithm

## 面试题3：数组中重复的数字

关键：每个位置放置的数字与下标对应相等

## https://leetcode.com/problems/merge-two-sorted-lists/

# Golang中闭包的实现原理

* 小结

1. Go语言能通过escape analyze识别出变量的作用域，自动将变量在堆上分配。将闭包环境变量在堆上分配是Go实现闭包的基础。

识别出变量需要在堆上分配，是由编译器的一种叫escape analyze的技术实现的。

2. 返回闭包时并不是单纯返回一个函数，而是返回了一个结构体，记录下函数返回地址和引用的环境中的变量地址。

3. 闭包的实现

前面说过，闭包是函数和它所引用的环境。那么是不是可以表示为一个结构体呢:
```
type Closure struct {
    F func() int
    i *int
}
```
> https://blog.csdn.net/skh2015java/article/details/87921438

Go 语言闭包详解

> https://www.sulinehk.com/post/golang-closure-details/


# go语言调度器源代码情景分析

## 预备知识

### 汇编指令

https://mp.weixin.qq.com/s?__biz=MzU1OTg5NDkzOA==&mid=2247483693&idx=1&sn=e5398ae82e2f3484bea5e8858b1a9cd7&scene=19#wechat_redirect

> http://www.ruanyifeng.com/blog/2018/01/assembly-language-primer.html

### 函数调用过程

* CPU是如何从调用者跳转到被调用函数执行的？

* 参数是如何从调用者传递给被调用函数的？

* 函数局部变量所占内存是怎么在栈上分配的？

* 返回值是如何从被调用函数返回给调用者的？

* 函数执行完成之后又需要做哪些清理工作？

> https://mp.weixin.qq.com/s?__biz=MzU1OTg5NDkzOA==&mid=2247483723&idx=1&sn=772960aa0d5ae4aa6921e9ff43fcb99f&scene=19#wechat_redirect

### Go语言调度器源代码情景分析之十：线程本地存储
go的runtime是如何利用线程本地存储来把正在运行的goroutine和工作线程关联在一起的。

## 正式分析

## Mac设置gbd

> https://pan.wps.cn/l/sAxfWHLi1

* gdb调试命令
> https://www.cnblogs.com/wuyuegb2312/archive/2013/03/29/2987025.html

* debug信息被压缩,在mac不可被识别. 需要设置环境变量，设置为不压缩

In Go 1.11, the debug information is compressed for purpose of reduce binary size, and gdb on the Mac does not understand compressed DWARF. 

```
export GOFLAGS="-ldflags=-compressdwarf=false"
```

不执行这个环境变量,会导致gdb读取不到压缩的debug信息

```
Reading symbols from main...
(No debugging symbols found in main)
Loading Go Runtime support.
```
> https://stackoverflow.com/questions/52534287/debug-go-program-with-gdb-on-macos

## gdb编译和调试

```
go build -gcflags "-N -l" -o xxx xxx.go
b main.main
// optional: set disassembly-flavor intel
disass main.main
```
> https://favoorr.github.io/2017/02/26/gdb-trace-go-function-call/

## Linux中修改环境变量及生效方法（永久、临时）环境变量查看

1. 在/etc/profile文件中添加变量【对所有用户生效（永久的）】  

2. 在用户目录下的.bash_profile文件中增加变量【对单一用户生效（永久的）】
要让刚才的修改马上生效，需要在用户目录下执行以下代码:

source .bash_profile  

3. 直接运行export命令定义变量【只对当前shell（BASH）有效（临时的）】  

> https://blog.csdn.net/u011630575/article/details/49839893

Mac OS X配置环境变量

> https://www.jianshu.com/p/7e30b7b7ee48
