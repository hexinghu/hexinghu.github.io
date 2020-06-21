---
title: VScode C/C++开发环境搭建
date: 2020-06-22 01:26:55
tags:
    - VSCODE
    - C/C++
---

## 在vscoe中搭建C/C++开发环境
大家都知道用VS来开发C/C++的话虽然很方便，但是VS太过于臃肿和庞大，而且它还是要收费的，也没有VSCode那么美观的主题，所以很多人都会想用VSCode来开发C/C++程序，那么怎么用VSCode来搭建C/C++开发环境呢？下面仔细来介绍一下。

1. 安装VsCode和MinGW64
安装VSCode非常简单，可以到[官网](https://code.visualstudio.com/#alt-downloads)去下载安装.安装好VScode之后接着安装MinGW64，可以到[这里](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/installer/mingw-w64-install.exe)下载安装，安装完成之后，把MinGW加入到系统环境变量（也可以在安装的时候就选择加入环境变量）。
2. 在VSCode中安装cpp插件
打开VScode软件，在扩展中搜索C/C++插件，安装好之后可以创建一个C/C++的工程文件夹，用VScode打开然后点击调试会自动生成一个.vscode的文件夹，这个文件夹里有一个lanch.json文件，再点击终端选择生成任务（选择默认模板即可）这时候会在.vscode文件夹下生成一个task.json文件。
* 配置lanch.json文件

```json
{
    "version": "0.2.0",
    "configurations": [
      {
        "name": "g++", //配置名称将会在下拉菜单中显示
        "type": "cppdbg", //配置类型，这里只能为cppdbg
        "request": "launch",//请求类型，这里可以为lanch(启动)或者attach(附件)
        "program": "${workspaceFolder}\\build\\${fileBasenameNoExtension}.exe",//编译后生成的可执行文件
        "args": [],//程序调试时传递给程序的命令行参数，一般设为空即可
        "stopAtEntry": false,// 设为true时程序将暂停在程序入口处，一般设置为false
        "cwd": "${workspaceFolder}",// 调试程序时的工作目录
        "environment": [],
        "externalConsole": true,// 调试时是否显示控制台窗口，一般设置为true显示控制台
        "MIMode": "gdb",
        "miDebuggerPath": "D:\\MinGW64\\mingw64\\bin\\gdb.exe",// miDebugger的路径，注意这里要与MinGw的路径对应
        "setupCommands": [
          {
            "description": "Enable pretty-printing for gdb",
            "text": "-enable-pretty-printing",
            "ignoreFailures": true
          }
        ],
        "preLaunchTask": "g++"
      }
    ]
}
```
* 配置task.json文件

```json
{
    "version": "2.0.0",
    "tasks": [
      {
        "type": "shell",
        "label": "g++",
        "command": "g++",
        "args": ["-g", "${file}", "-o", "${workspaceFolder}\\build\\${fileBasenameNoExtension}.exe"],
        "problemMatcher": ["$gcc"],
        "group": {
          "kind": "build",
          "isDefault": true
        }
      }
    ]
  }
```
配置玩这两个文件之后就可以编写C/C++文件并调试运行了。
