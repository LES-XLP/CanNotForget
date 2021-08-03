### VSCODE配置文件现用版本

#### c_cpp_properties.json
```
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**",
                "D:/Software/Mingw64/lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++",
                "D:/Software/Mingw64/lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++/x86_64-w64-mingw32",
                "D:/Software/Mingw64/lib/gcc/x86_64-w64-mingw32/8.1.0/include/c++/tr1",
                "D:/Software/Mingw64/lib/gcc/x86_64-w64-mingw32/8.1.0/include",
                "D:/Software/Mingw64/include"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            "cStandard": "c17",
            "cppStandard": "c++17",
            "intelliSenseMode": "windows-msvc-x64",
            
            "browse": {
                "path": [
                    "${workspaceRoot}",
                    "D:/Software/Mingw64/x86_64-w64-mingw32/lib",
                    "D:/Software/Mingw64/x86_64-w64-mingw32/include"

                ],
                "limitSymbolsToIncludedHeaders": true,
                "databaseFilename": ""

            }

        }
    ],
    "version": 4
}
```
#### extensions.json
```
{
    "recommendations": [
        "github.vscode-pull-request-github"
    ]
}
```

#### launch.json
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) 启动",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceRoot}/${fileBasenameNoExtension}",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "preLaunchTask": "Compile" ,
            "MIMode": "gdb",
            "miDebuggerPath": "D:/Software/Mingw64/bin/gdb.exe",
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

#### setting.json
```
{
    "files.associations": {
        "stdio.h": "c",
        "Structural04.C": "cpp",
        "cstdlib": "c"
    }
}
```

#### tasks.json
```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Compile" ,
            "command": "gcc",
            "args": [
                "${file}", 
                // 多文件编译部分
                // "${fileDirname}/add/add.c",
                // "${fileDirname}/sub/sub.c",
                // "${fileDirname}/mul/mul.c",
                // "${fileDirname}/dev/dev.c",  
                "-o", // 指定输出文件名，不加该参数则默认输出a.exe，Linux下默认a.out
                "${fileDirname}/${fileBasenameNoExtension}.exe",//选择输出的文件名称，和前面的${file}是对应的，一般默认的名称就是前面的${file}.exe
                "-g", // 生成和调试有关的信息
                "-Wall", // 开启额外警告
            ], 
            "type": "shell", // process是把预定义变量和转义解析后直接全部传给command；shell相当于先打开shell再输入命令，所以args还会经过shell再解析一遍
            "group": {
            "kind": "build",
            "isDefault": true // 不为true时ctrl shift B就要手动选择了
            },
            "problemMatcher":"$gcc"
        }
        
    ]
}
```
