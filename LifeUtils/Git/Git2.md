# Git使用

[toc]

## 跨团队合作

1. 首先fork到自己的远程库
2. 将远程库clone到本地库
3. 修改缓存区
4. add到暂存区
5. commit到本地仓库
6. push到远程仓库
7. 在远程库pull request，发送给原团队
8. 原团队审核代码
9. merge操作
10. 将远程库pull到本地仓库

## SSH登录

1. ssh-keygen -t rsa -C 邮箱
2. 进入~/.ssh/id_rsa.pub
3. 复制公钥
4. 添加到git账号的sshkey
5. ssh -T git@github.com

## git merge的"Fast forward"模式

    git merge通常比较快，默认使用“Fast forward”模式，在这种模式下，删除分支后，会丢掉分支信息，使用--no-ff禁用“Fast forward”模式。

示例：

![git merge的fast forward模式](./.img/Git2GitMergeFF.jpeg)

## git stash
