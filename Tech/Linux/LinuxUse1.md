# Linux基础命令

## 快捷命令



## 常見操作

### ln
#### ln的基本參數

```shell
ln -s link file 創建軟連接，軟連接指向file原本的inode，通過inode指向數據塊。
ln  inode file 創建硬連接，創建新的inode a指向file 原來的inode B 指向的數據塊c。原來的數據塊c的引用+1。(硬鏈接是不允許跨文件系統；硬鏈接的對象不允許爲文件目錄)

ln -n 檢驗軟連接是否被重復定義
ln -f 強制運行
ln -d 對目錄進行硬鏈接(對於超級管理員是可以建立硬鏈接；針對於目錄的硬鏈接是考慮到進行文件文件系統遍歷的過程中陷入死循環，而軟鏈接可以通過文件類型簡單判斷)

```

### history
#### history的基本參數
```shell
history存储输入的命令，默认存储100条
history -d offset 删除对应的offset
history -c 清空history
history -n 打印n条command
history -a 将缓冲区的命令添加到历史命令文件(/root/.bash_history)
history -w 将当前的command添加到历史命令文件
```
#### history的使用

+ 运行history的命令
```shell
!offset 运行对应offset的命令
!!  运行上一条命令
!?string 查找相似的命令，并且运行
fc offset 编辑history中对应的offset
```

+ 为history添加时间

export HISTTIMEFORMAT=‘%F％Ｔ’
export $HISTSIZE=num 修改history的size（默认1000）