## git 常见命令

```go
在本地初始化一个 git 仓库：
	git init
当前目录的本地仓库 关联 指定的远程仓库，并起别名：
	git remote add [远程仓库别名] [远程仓库 git 地址]

将本地代码提交到暂存区：
	1、git add [文件名]：提交某个添加/修改的文件
	2、git add -A：提交所有添加/修改的文件
将暂存区代码提交到版本库：
	1、git commit -m "注释信息"					    // 将所有 add 的文件都 commit，附带 commit 信息
	2、git commit -o [文件名1] [文件名2] -m "注释信息" // 指定已经 add 了的文件进行 commit
将版本库代码提交到远程仓库：
	1、git push origin [本地分支名]:[远程分支名]  // 将 origin 项目下某个分支下 commit 了的文件 push到指定的的远程分支
	2、git push origin [本地分支名] 			  // 本地分支名与远程分支名相同，可以省略一个

查看分支 
	git branch [-a]
切换分支 
	git checkout [本地分支名]
创建本地分支 
	git branch [branch_name]
删除本地分支 
	git branch -d [branch_name]

修改已经 commit 的注释：
	git commit --amend	//执行完命令后会进入 vim，此时原来的注释在第一行，可以直接进行修改，修改完后执行 wq 保存退出
	
撤销 commit,回到 add 状态
	git reset --soft HEAD~1
撤销 commit 和 add 状态，回到未 add 的状态
	1、git reset --mixed HEAD~1
	2、git reset HEAD^
撤销已经 commit 的 commit，并且删除修改的代码，回到上一个 commit 版本的状态
	git reset --hard HEAD^
//HEAD^ 等同于 HEAD~1 ,表示上一个版本


查看本地 git 仓库关联的是哪个远程仓库地址：
	git remote -v
```



## 工作区、暂存区、版本库

```
工作区：本地文件存储的位置

暂存区：git add 后文件存储的位置，所有的分支共享一个暂存区，即 分支A git add 后的文件别的分支也能看到，同时别的分支可以执行 git commit 将暂存区的文件变成自己的

版本库：git commit 后暂存区的文件存储的位置，每个分支都有一个版本库，谁执行了 commit，那么 commit 的文件只能被该分支看到，即没执行 commit 之前，所有分支都能看到一个 b.txt，分支A 执行了 commit 之后，其他分支都看不到这个 b.txt 了，只有分支A 看得到

```





## Push（推送）失败，出现版本冲突

[解决 git 冲突](https://blog.csdn.net/programerxiaoer/article/details/78585301)

[git 冲突产生的原因](https://blog.csdn.net/weixin_41287260/article/details/89742151)

问题：

Push 失败，提示 `non-fast-forward`

该问题就是，远程仓库的代码被修改过了，而你又没有拉取进行更新，然后你又自己修改了远程仓库被修改过的代码，然后要提交到远程仓库，git 发现你此时修改的代码不是基于最新的代码的，所以会拒绝推送，需要自己拉取代码，解决冲突后才能推送

*![image.png](https://pic.leetcode-cn.com/1615786616-DktDbE-image.png)*

解决：

```shell
// 1. 获取远程分支的修改
git fetch origin feature/milkouyang_862546847
// 2. 合并远程分支
git merge origin feature/milkouyang_862546847
// 3. 更新本地分支
git pull origin feature/milkouyang_862546847
```

此后会提示冲突的内容，手动解决即可