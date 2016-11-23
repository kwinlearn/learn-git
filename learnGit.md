# Git 常用命令
#### 创建版本库 (repository)
```
init git
```
#### 设置用户名及邮箱
```
git config [--global] user.name "your name"
git config [--global] user.email "your email"
```
#### 查看仓库当前状态
```
git status
```
#### 将文件信息添加到索引库
```
git add fileName
git add -A [path]                       //表示把path中所有tracked（跟踪）文件中被修改过或已删除文件和所有untracted的文件信息添加到索引库  省略path表示 "." 当前路径下
git add -u [path]                       //把path中所有tracked文件中被修改过或已删除文件的信息添加到索引库。它不会处理untracted的文件。
查看path中被所有修改过或已删除文件但没有提交的文件，
并通过其revert子命令可以查看path中所有untracted的文件，同时进入一个子命令系统。
git add -i [path]                       
```
#### 根据索引库将文件提交到仓库
```
git commit -m "commit message"
```
#### 查看文件修改差异
```
git diff fileName
```
#### 查看提交日志（按时间倒序排列）
```
git log [--pretty=oneline]
```
#### 版本恢复回退命令
```
git reset -mixed                        //默认方式，回退到某个版本，保留commit之前源码，回退commit和index信息
git reset –soft                         //回退到某个版本，只回退了commit的信息，不会恢复到index file一级。如果还要提交，直接commit即可
git reset –hard                         //彻底回退到某个版本，撤销commit，撤销添加到index索引的文件

回退所有内容到上一个版本 
git reset HEAD^ 
//回退a.py这个文件的版本到上一个版本 
git reset HEAD^ a.py 
向前回退到第3个版本 
git reset –soft HEAD~3 
git reset –soft HEAD^^^
将本地的状态回退到和远程的一样 
git reset –hard origin/master 
回退到某个版本 
git reset commitId 
回退到上一次提交的状态，按照某一次的commit完全反向的进行一次commit 


撤销 某次操作，此次操作之前和之后的commit和history都会保留，并且将制定版本撤销
撤销制定commit，作为一个新commit
git revert HEAD
git revert commitId
```
#### 误操作 reset --hard
```
git reset --hard 误操作版本号
```
#### 操作日志
```
git reflog
```

//将工作区中文件的修改（包括删除）撤销
```
git checkout -- fileName

分为两种情况：
    a. 文件自从修改后还没有commit到索引(index)，撤销后就回到和版本库一模一样的状态
    b. 已经添加到暂存区后，又作了修改，撤销修改就回到添加到暂存区后的状态
```