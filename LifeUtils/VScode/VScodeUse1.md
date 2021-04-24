# VScode使用过程中的问题

[toc]

## 设置VScode配置文件(Ubuntu)
+ luanch.json

    默认文件如下：

        // Use IntelliSense to learn about possible attributes.
        // Hover to view descriptions of existing attributes.
        // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
        "version": "0.2.0",
        "configurations": [
            {
                "name": "(gdb) Launch",
                "type": "cppdbg",
                "request": "launch",
                "program": "enter program name, for example ${workspaceFolder}/a.out",
                "args": [],
                "stopAtEntry": false,
                "cwd": "${workspaceFolder}",
                "environment": [],
                "externalConsole": true,
                "MIMode": "gdb",
                "setupCommands": [
                    {
                        "description": "Enable pretty-printing for gdb",
                        "text": "-enable-pretty-printing",
                        "ignoreFailures": true
                    }
                ]
            }
        ]
    }

    修改部分：

        "program": "${workspaceFolder}/${fileBasenameNoExtension}.out"

+ tasks.json

默认文件如下：

    {
        // See https://go.microsoft.com/fwlink/?LinkId=733558
        // for the documentation about the tasks.json format
        "version": "2.0.0",
        "tasks": [
            {
                "label": "echo",
                "type": "shell",
                "command": "echo Hello"
            }
        ]
    }

修改部分：

label：任务名，”label"= "echo"改为”label"= "build"。
command：执行的命令，”command“=”echo Hello“改为”command“=”g++“，添加g++的参数args。
**如果指令为：g++ -g main.cpp**

    {
        "tasks": [
            {
                "label": "build",
                "type": "shell",
                "command": "g++",
                "args": ["-g", "${file}"]
            }
        ]
    }
**如果指令为：g++ -g main.cpp -std=c++11 -o main.out**

    {
        "tasks": [
            {
                "label": "build",
                "type": "shell",
                "command": "g++",
                "args": ["-g", "${file}", "-std=c++11", "-o", "${fileBasenameNoExtension}.out"]
            }
        ]
    }

## 