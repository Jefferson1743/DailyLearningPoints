# Git
## Git介绍

Git分为四个部分：
+ Workspace：工作区
+ Index / Stage：暂存区
+ Repository：仓库区（或本地仓库）
+  Remote：远程仓库

![git流程](./.img/Git1GitIntroduce.jpeg)

## Git相关命令

    git init 初始化
    git config
        设置系统用户级别签名
            git config --global user.name "jefferson"
            git config -- global user.email "jefferson@163.com"
            配置文件：项目目录下的./.git/config文件
        设置项目级别签名(项目级别高于系统用户级别)：
            git config user.name "jeff"
            git config user.email "jeff@163.com"
            配置文件：家目录下的gitconfig文件
        git config --list 查看所有信息
        git config --global core.quotepath false   应对中文无法显示
    git status  查看工作去和暂存区的状态
    git add     将工作区的新建和修改提交到暂存区
    git commit  
        git commit -m "commit message" 文件名 将暂存区的文件提交到本地仓库(-m 可以避免进入vim，直接添加备注信息)
        git commit -am "commit message" 文件名  将工作区的文件直接提交到本地仓库
    git log
        git log 提交到本地仓库的历史
        git log --pretty=oneline    以优美的形式显示，每条日志信息只显示一条
        git log --oneline   以优美的形式显示，每条日志信息只显示一条
    git reflog  显示日志，显示指针回退的步数
    git reset(hard)
        git reset --hard:
            在本地库移动HEAD指针
            重置暂存区
            重置工作区
            如果只是在暂存区和工作区删除，并没有提交到本地库。可以使用git reset --hard HEAD，回退到赏赐commit的版本
        git


        

            
        git reset HEAD 局部索引值     回退到具体的局部索引
        git reset --hard HEAD~n     回退n步 
        git reset --hard HEAD^^^    回退三步
        git reset HEAD




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
