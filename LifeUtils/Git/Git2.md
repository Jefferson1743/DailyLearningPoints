# Git相关知识

## .gitignore文件
简介：

    .gitignore主要用于过滤文件，不用push到github的远程库中。

文件内容：

    # Built application files
    *.apk
    *.aar
    *.ap_
    *.aab
    
    # Java class files
    *.class

    # Folder
    /bin/

    # File
    /bin/start.cpp

配置语法：

    以/开头：表示目录
    *：通配多个字符
    ?：通配单个字符
    []：单个字符的匹配列表
    !：不忽略某个文件或者目录
    注：
        /folder/ 忽略folder文件夹
        *.cpp   忽略cpp结尾的文件
        start.? 忽略start. 文件
        start.[a, b, c] 忽略start.a, start.b, start.c 文件
        !start.c    不忽略start.c文件
