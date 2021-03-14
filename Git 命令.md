## git 命令

```shell
在本地初始化一个 git 仓库：git init
当前目录的本地仓库 关联 指定的远程仓库：git remote add origin [远程仓库 git 地址]
	//这个 origin 实际上是给远程仓库的别名，我们操作 origin 实际上就是在操作远程仓库，一般别名都是直接叫 origin

将本地代码提交到暂存区：git add [文件名] / git add -A
将暂存区代码提交到版本库：git commit -m "注释信息"
将版本库代码提交到远程仓库：git push origin [本地分支名] : [远程分支名] / git push origin [远程分支名]


查看分支 git branch [-a]
切换分支 git checkout [branch_name]
创建本地分支 git branch [branch_name]
删除本地分支 git branch -d [branch_name]
push 本地分支到远程分支：git push origin [local-branch] : [remote-branch]

修改已经 commit 的注释：git commit --amend
	//执行完命令后会进入 vim，此时原来的注释在第一行，可以直接进行修改，修改完后执行 wq 保存退出
	
撤销 commit 和 add 状态	git reset --mixed HEAD^ / git reset HEAD^
撤销 commit 回 git add 状态，仍然保留修改的代码：git reset --soft HEAD^
撤销 commit，并且删除修改的代码，回到上一个 commit 版本的状态：git reset --hard HEAD^
	//HEAD^ 表示上一个版本
```



## 工作区、暂存区、版本库

```
工作区：本地文件存储的位置

暂存区：git add 后文件存储的位置，所有的分支共享一个暂存区，即 分支A git add 后的文件别的分支也能看到，同时别的分支可以执行 git commit 将暂存区的文件变成自己的

版本库：git commit 后暂存区的文件存储的位置，每个分支都有一个版本库，谁执行了 commit，那么 commit 的文件只能被该分支看到，即没执行 commit 之前，所有分支都能看到一个 b.txt，分支A 执行了 commit 之后，其他分支都看不到这个 b.txt 了，只有分支A 看得到
```

