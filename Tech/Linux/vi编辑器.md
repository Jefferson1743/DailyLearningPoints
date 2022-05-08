# vi编辑器
## 三种模式
+ 命令模式
+ 编辑模式
+ 末行模式
## 命令模式
常见快捷键

## 末行模式
    ：q   没有修改，直接退出
    ：wq  拥有写权限，保存修改，退出文件  
    ：q!  修改后不保存退出  
    ：n1, n2 w filename n1~n2行的内容保存到filename文件中
    ：n1, n2 co n3  n1~n2行的内容复制到n3行
    ：!command  暂时离开vi，执行command命令

    ：setnu 设置行号
    ：setnonu 取消行号
    ：vs filename 
    ：sp filename
    Del 在可视快模式下，一次删除所选内容
    r   在可视块模式下，一次性替换所选的内容
    无修改权限修改后，后无法
