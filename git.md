## 工程准备 git init & git clone

git init 用于在本地新建git仓库

```bash
git init firstProject
```

git clone 用于克隆远端仓库

```bash
git clone [URL]
```

## 常用操作

git commit 将暂存区里的文件改动提交到本地的版本库

```bash
git commit file_name -m "commit message"

//批量提交
git commit -am "commit message"
```

git log 用于查看提交历史

```bash
git log
```

将本地仓库关联到远程仓库。

自己fork的仓库可以用origin，源仓库可以用upstream

```bash
//origin是给关联的远程仓库起的别名
git remote add origin [远程仓库地址]
git remote -v //查看关联的远程仓库
```

使用git commit命令将自己的修改内容从暂存区提交到本地版本库以后，可以使用git push将本地版本库的分支推送到远程服务器上对应的分支

```bash
//推送之前可以使用git remote -v 先查看一下
git push origin branch_name

//本地分支名也可以和推送到远端的分支名不同
git push origin branch_name:new_branch_name
```

git branch 命令可以查看本地工程的所有git分支名称

### 分支管理

```bash
git branch//查看本地分支

git branch -r //查看远端服务器上的分支

git branch -a //查看远端服务器和本地工程所有的分支

git branch new_branch_name//新建分支后不会切换到新分支
git checkout -b new_branch_name//新建分支后会自动切换到新分支
//两者都是基于当前分支的节点创建新分支的

git branch -d 和 git branch -D 都可以用来删除本地分支，后者大写表示强制删除

//删除远端分支，注意这里要推送到远端
git branch -d -r branch_name
git push origin:branch_name

git checkout [-f] branch_name //切换分支，检出  -f可以强制切换
```

### git pull && fetch

git pull的作用是从远端服务器获取某个分支的更新，再与本地自动合并

而fetch不会自动合并

```bash
git pull origin remote_branch:local_branch
git pull origin remote_branch

git fetch origin remote_branch:local_branch
git fetch origin remote_branch
```

```bash
//在本地新建一个temp分支，并将远程origin仓库的master分支代码下载到本地temp分支
git fetch origin master:tmp 

//来比较本地代码与刚刚从远程下载下来的代码的区别
git diff tmp 

//合并temp分支到本地的master分支
git merge tmp

//如果不想保留temp分支 可以用这步删除
git branch -d temp
```

```bash
//获取远程主机某个分支的更新，再与本地的指定分支合并。
git pull <远程主机名> <远程分支名>:<本地分支名>
```

### git merge

```bash
//执行以下代码块
git checkout feature
git merge master

//或者直接合并
git merge master feature
```

