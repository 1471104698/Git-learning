## git 命令

```shell
查看分支 git branch [-a]
切换分支 git checkout [branch_name]
创建本地分支 git branch [branch_name]
删除本地分支 git branch -d [branch_name]
push 本地分支到远程分支：git push origin [local-branch] : [remote-branch]

修改已经 commit 的注释：git commit --amend
	执行完命令后会进入 vim，此时原来的注释在第一行，可以直接进行修改，修改完后执行 wq 保存退出
	
撤销 commit 和 add 状态	git reset --mixed HEAD^ / git reset HEAD^
撤销 commit 回 git add 状态，仍然保留修改的代码：git reset --soft HEAD^
撤销 commit，并且删除修改的代码，回到上一个 commit 版本的状态：git reset --hard HEAD^
```



