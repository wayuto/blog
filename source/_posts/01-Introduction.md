---
title: 01-Introduction
date: 2026-02-26 23:25:16
tags:
---
# 介绍
`Alum`语言是一门静态类型，语法接近`C`与`Rust`，运行在x86_64 Linux平台的语言，对`C`语言有良好的兼容性，性能接近C(Benchmark: fib(30)), 由笔者使用`Rust`独立开发。

## Hello world
这是每个语言经典的第一个程序，对于`Alum`, 最简单的Hello world如下
```Alum
$import "io.al" // 引入标准I/O函数(print, input, open, close, ...)

fun main() { // Alum语言的函数入口，与大多数语言一致
    println("Hello world!") // print不换行，println自动换行
    return 0 // 返回程序退出状态码
}
```
将其保存为.al文件，并用alc编译运行，即可得到输出
```bash
$ alc hello.al
$ ./hello.al
```
程序输出结果为：
```
Hello world!
```

## Alum语言的来源
笔者之前看过许多解释器的实现，包括`LLVM`的示例语言(Kaleidoscope)，以及类似C的虚拟机，但归根结底还是别人的东西，不如自己动手实现一个，下学回家的路上，灵光一现，想到最近刚学`TypeScript`，不如写个项目联系一下，于是我便想到了实现一个解释器，没错初版`ALum`实际上是由`TypeScript`实现的解释性语言，并且名字也不叫`Alum`，而是`Gos`（Deno的包仓库还能找到），他们都没有特殊含义，只是看着很顺眼，仅此而已。  
在`Gos` 0.5.x(大概)版本，正式改名为`Alum`，并专注于编译器的实现，抛弃了GVM(GosVM)，虽然是因为懒得写解释器了……  
初代的编译器并非使用Cranelift, 而是通过后端输出汇编的方式，依赖NASM与GNU Linker生成二进制文件，考虑到跨平台性（虽然也没有跨平台），复杂性与可维护性，通过现代高新技术(AI)使用Cranelift进行了大规模重构，并重写了编译器前端（其实只是加了Result）。