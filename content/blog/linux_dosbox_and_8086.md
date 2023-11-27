---
title: "在linux中使用dosbox搭建8086汇编环境"
date: 2023-11-26
description: "在linux中使用dosbox搭建8086汇编环境,以及masm.exe和debug.exe的使用"
---

最近在学 8086 汇编，还要用它写作业（主要是 masm），所以要自己的电脑上搞一个能写 masm 的环境。查了一会资料，
勉强可以用了，记录一下

## 写汇编要用到的

- 汇编器 masm.exe
- 连接器 linker.exe
- 调试器 debug.exe
- 以上三个都不能在 linux 下直接运行，所以需要一个虚拟环境，dosbox

## 安装

**安装 Dosbox**

```bash
#Arch linux
sudo pacman -S dosbox
```

**安装汇编器三件套**
找了半天都找不到资源，

## 启动 dosbox

直接在命令行输入 dosbox 即可启动

进入后要将 c 盘挂载在一个目录下

```cmd
mount c /path/to/masm
C:
```

然后就可以汇编连接开写了

另外每次关闭 dosbox 在重新打开,都要 mount,好在可以在配置文件中设置

配置文件的位置就在启动 dosbox 的说明中

```
dosbox
    DOSBox version 0.74-3
    Copyright 2002-2019 DOSBox Team, published under GNU GPL.
    ---
    CONFIG:Loading primary settings from config file /PATH/TO/DOSBOX/CONF
    ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
    MIDI:Opened device:none

```

把 mount 的命令添加进去

```conf
...
[autoexec]
mount /path/to/masm
C:
```

现在就可以在 dosbox 中使用 masm 啦
