# C Class Helper

## 简介 | Brief Intro

[仓库地址 | Github Repo Address](https://github.com/IsshikiHugh/C-Class-Helper)

这是一个为 C 语言学习新手提供的一个日志打印工具，整体功能比较简单，目的是培养刚接触编程的同学学习和养成 Debug 正确方法和好习惯。

## 使用 | Usage

### 导入 | Import

- 对于尚在学习单文件编程的同学，我们建议你直接复制`CClassHelper.h`中的所有内容至你的代码的最前。
- 对于已经知道如何进行多模块编程的同学，我们建议您直接`#include "CClassHelper.h"`

### 输出一般日志 | Log

使用`LOG(...)`来输出一般日志。
- `LOG()`的使用方法和`printf()`基本一致，只需要把`printf()`语句中的函数名换成`LOG`即可。

举个例子：

如果您想在某一处输出一条日志语句：

```c
    char myCharArr[] = "It's OK!";
    LOG("This is a log message. %s", myCharArr);
```
> 这里的`;`并不是必要的，但是个人建议加上，这样比较好看。

### 监控变量 | Variable Monitor

使用`SHOW_VAR(CCH_TYPE, CCH_VAR)`来监控变量。
- 其中`CCH_TYPE`指对应变量在`printf()`的 format 中所使用的占位符，例如`int`对应的`CCH_TYPE`为`"%d"`，`double`对应的`CCH_TYPE`为`"%lf"`；
  - 当然，由于该宏函数的底层使用的是`printf()`，所以实际上相关的扩展语法都是支持的。比如`"%.2lf"`
- `CCH_VAR`指对应变量；

举个例子：

如果您想在某一处监控`int`类型变量`x`，则在该位置写上：

```c
    SHOW_VAR("%d", x);
```
> 这里的`;`并不是必要的，但是个人建议加上，这样比较好看。

### 监控数组 | Array Monitor

使用`SHOW_ARR(CCH_TYPE, CCH_ARR_NAME, CCH_ARR_BEGIN, CCH_ARR_END)`来监控数组。
- 其中`CCH_TYPE`指对应变量在`printf()`的 format 中所使用的占位符，同上；
- `CCH_ARR_NAME`指数组名，例如`int a[10];`中的`a`；
- `CCH_ARR_BEGIN`和`CCH_ARR_END`分别为需要监控的数组的始末下表，且**左闭右开**；
  - 具体来说，比如为想监控`a[0]` `a[1]` `a[2]` `a[3]` ... `a[9]`，那么对应的`CCH_ARR_BEGIN`为`0`，`CCH_ARR_END`为`10`；
  - 换句话来说，这个宏函数只能用来监控一维数组的连续段；

举个例子：

如果您想在某一处监控`int`类型数组`a[]`，范围是`a[0]`到`a[10]`，则在该位置写上：

```c
    SHOW_ARR("%d", a, 0, 10);
```
> 这里的`;`并不是必要的，但是个人建议加上，这样比较好看。

## 后续计划

- [ ] 输出为日志文件
- [ ] 支持正常 terminal 下的彩色字体
- [ ] 支持 Windows CMD 下的彩色字体
- [ ] 尝试解决多维数组的监控方案
- [ ] 在监控变量时支持自定义注解语句（目前已经能够实现，但是是否有更优雅的解法）
- [ ] ...