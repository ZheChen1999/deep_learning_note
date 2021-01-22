<center><span style="font-size:3rem;font-weight:bold;">Git学习笔记-2021.1.19</span></center>

| 版本     | 作者   | 时间        | 备注        |
| ------ | ---- | --------- | --------- |
| V1.0.0 | 陈哲   | 2021.1.19 | Git入门学习笔记 |



<div style="page-break-after: always;"></div>

[TOC]



<div style="page-break-after: always;"></div>



# Git download

[下载地址](https://npm.taobao.org/mirrors/git-for-windows/)，我选用的是淘宝的镜像，这个比较快。

# Let's start a project

## Git global setup

> `git config --global user.name "chenzhe"`   自己的用户名
>
> `git config --global user.email "chenzhe@rockontrol.com"`自己的邮箱



## Create a new repository

> `git clone git@git.querycap.com:1351387980283281414/test.git` 
>
> > 克隆gitlab上的项目到本地
>
> `cd test`
>
> `touch README.md`
>
> `git add README.md`  
>
> > 添加到暂存区
>
> `git commit -m "add README"`
>
> > 把文件提交到仓库
>
> `git push -u origin master`

## Push an existing folder

> `cd existing_folder`
>
> `git init`  
>
> > 把这个目录变成git可以管理的仓库,会多了一个.git的目录，是Git来跟踪管理版本的，没事千万不要手动乱改这个目录里面的文件，否则，会把git仓库给破坏了
>
> `git remote add origin git@git.querycap.com:1351387980283281414/test4.git`
>
> `git add .` 
>
> `git commit -m "Initial commit"`
>
> `git push -u origin master`

## Push an existing Git repository

> `cd existing_repo`
>
> `git remote rename origin old-origin`
>
> `git remote add origin git@git.querycap.com:1351387980283281414/test4.git`
>
> `git push -u origin --all`
>
> `git push -u origin --tags`

# Git basical command 

## Branch

* Build a new branch: `$ git branch testing` 

  > 新建一个testing分支

* Change another branch：`$ git checkout testing`

  > 切换到另一个testing分支

* Merge branch：`$ git merge` 

  > 分支的合并

* Rebase branch：

  `$ git checkout test  `

  `$ git rebase master` 

  > 分支的衍合，就可以把在test分支里提交的改变移到master分支里重放一遍。

* Delete branch：`$ git branch -d testing`

  > 删掉testing分支

* View history log:`$ git log`

  > 查看历史操作过程

  ​

## Git configuration

```shell
# 配置提交记录中的用户信息
$ git config --global user.name <用户名>
$ git config --global user.email <邮箱地址>
# 配置长期存储密码
$ git config --global credential.helper store
# 查看当前生效的配置信息
$ git config -l
# 编辑配置文件
# --local：仓库级，--global：全局级，--system：系统级
$ git config <--local | --global | --system> -e
```

## Git clone

从远程仓库克隆一个版本库到本地。

```shell
# 默认在当前目录下创建和版本库名相同的文件夹并下载版本到该文件夹下
$ git clone <远程仓库的网址>

# 指定本地仓库的目录
$ git clone <远程仓库的网址> <本地目录>

# -b 指定要克隆的分支，默认是master分支
$ git clone <远程仓库的网址> -b <分支名称> <本地目录>
```

## Git init

初始化项目所在目录，初始化后会在当前目录下出现一个名为 .git 的目录。

```shell
# 初始化本地仓库，在当前目录下生成 .git 文件夹
$ git init
```

## Git remote

操作远程库。

```shell
# 列出已经存在的远程仓库
$ git remote

# 列出远程仓库的详细信息，在别名后面列出URL地址
$ git remote -v
$ git remote --verbose

# 添加远程仓库
$ git remote add <远程仓库的别名> <远程仓库的URL地址>

# 修改远程仓库的别名
$ git remote rename <原远程仓库的别名> <新的别名>

# 删除指定名称的远程仓库
$ git remote remove <远程仓库的别名>

# 修改远程仓库的 URL 地址
$ git remote set-url <远程仓库的别名> <新的远程仓库URL地址>
```

## Git add

把要提交的文件的信息添加到暂存区中。当使用 git commit 时，将依据暂存区中的内容来进行文件的提交。

```shell
# 把指定的文件添加到暂存区中
$ git add <文件路径>

# 添加所有修改、已删除的文件到暂存区中
$ git add -u [<文件路径>]
$ git add --update [<文件路径>]

# 添加所有修改、已删除、新增的文件到暂存区中，省略 <文件路径> 即为当前目录
$ git add -A [<文件路径>]
$ git add --all [<文件路径>]

# 查看所有修改、已删除但没有提交的文件，进入一个子命令系统
$ git add -i [<文件路径>]
$ git add --interactive [<文件路径>]
```

## Git commit

将暂存区中的文件提交到本地仓库中。

````shell
#把暂存区中的文件提交到本地仓库，调用文本编辑器输入该次提交的描述信息
$ git commit
#把暂存区中的文件提交到本地仓库中并添加描述信息
$ git commit -m "<提交的描述信息>"
#把所有修改、已删除的文件提交到本地仓库中
#不包括未被版本库跟踪的文件，等同于先调用了 "git add -u"
$ git commit -a -m "<提交的描述信息>"
#修改上次提交的描述信息
$ git commit --amend
````

## Git fetch

从远程仓库获取最新的版本到本地的 tmp 分支上。

```shell
# 将远程仓库所有分支的最新版本全部取回到本地
$ git fetch <远程仓库的别名>

# 将远程仓库指定分支的最新版本取回到本地
$ git fetch <远程主机名> <分支名>
```

## Git merge

合并分支。

```shell
# 把指定的分支合并到当前所在的分支下
$ git merge <分支名称>
```

## Git diff

比较两个版本之间的差异。

```shell
# 比较当前文件和暂存区中文件的差异，显示没有暂存起来的更改
$ git diff

# 比较暂存区中的文件和上次提交时的差异
$ git diff --cached
$ git diff --staged

# 比较当前文件和上次提交时的差异
$ git diff HEAD

# 查看从指定的版本之后改动的内容
$ git diff <commit ID>

# 比较两个分支之间的差异
$ git diff <分支名称> <分支名称>

# 查看两个分支分开后各自的改动内容
$ git diff <分支名称>...<分支名称>
```

## Git pull

从远程仓库获取最新版本并合并到本地。
首先会执行 `git fetch`，然后执行 `git merge`，把获取的分支的 HEAD 合并到当前分支。

```shell
# 从远程仓库获取最新版本。
$ git pull
```

## Git push

把本地仓库的提交推送到远程仓库。

```shell
# 把本地仓库的分支推送到远程仓库的指定分支
$ git push <远程仓库的别名> <本地分支名>:<远程分支名>

# 删除指定的远程仓库的分支
$ git push <远程仓库的别名> :<远程分支名>
$ git push <远程仓库的别名> --delete <远程分支名>
```

## Git reset

还原提交记录。

```shell
# 重置暂存区，但文件不受影响
# 相当于将用 "git add" 命令更新到暂存区的内容撤出暂存区，可以指定文件
# 没有指定 commit ID 则默认为当前 HEAD
$ git reset [<文件路径>]
$ git reset --mixed [<文件路径>]

# 将 HEAD 的指向改变，撤销到指定的提交记录，文件未修改
$ git reset <commit ID>
$ git reset --mixed <commit ID>

# 将 HEAD 的指向改变，撤销到指定的提交记录，文件未修改
# 相当于调用 "git reset --mixed" 命令后又做了一次 "git add"
$ git reset --soft <commit ID>

# 将 HEAD 的指向改变，撤销到指定的提交记录，文件也修改了
$ git reset --hard <commit ID>
```

## Git revert

生成一个新的提交来撤销某次提交，此次提交之前的所有提交都会被保留。

```shell
# 生成一个新的提交来撤销某次提交
$ git revert <commit ID>
```

## Git rm

删除文件或者文件夹。

```shell
# 移除跟踪指定的文件，并从本地仓库的文件夹中删除
$ git rm <文件路径>

# 移除跟踪指定的文件夹，并从本地仓库的文件夹中删除
$ git rm -r <文件夹路径>

# 移除跟踪指定的文件，在本地仓库的文件夹中保留该文件
$ git rm --cached
```

## Git cherry-pick

把已经提交的记录合并到当前分支。

```shell
# 把已经提交的记录合并到当前分支
$ git cherry-pick <commit ID>
```

## Git tag

操作标签的命令。

``` shell
#打印所有的标签
$ git tag <标签名称> [<commit ID>]

#添加带有描述信息的附注标签，可以指定之前的提交记录
$ git tag -a <标签名称> -m <标签描述信息> [<commit ID>]

#切换到指定的标签
$ git checkout <标签名称>

#查看标签的信息
$ git show <标签名称>

#删除指定的标签
$ git tag -d <标签名称>

#将指定的标签提交到远程仓库
$ git push <远程仓库的别名> <标签名称>

#将本地所有的标签全部提交到远程仓库
$ git push <远程仓库的别名> –tags 
```

## Git submodule

Git Submodule 允许一个git仓库，作为另一个git仓库的子目录，并且保持父项目和子项目相互独立。使用git管理的项目开发中，如果碰到公共库和基础工具，可以用submodule来管理。

例如：

* 公共库是`lib.git`， 地址：`git@github.com:lib.git`
* 需要使用公共库的项目是`proj.git`，地址：`git@github.com:proj.jit`



 ### Add a submodule

 `$ git submodule add git@github.com:lib.git <local path>` 其中，<local path>是需要保存的目录名

该命令实际会做三件事情：首先，clone `lib.git`到本地；然后，创建一个 `.gitsubmodule` 文件标记submodule的具体信息；同时，更新`.git/config`文件，增加submodule的地址：

### delete a submodule

首先，需要删除 `.git/config` 和 `.gitsubmodle` 文件里submodule相关的部分，然后执行：

```shell
$ git rm --cached <local path>
```

才能将submodule的相关文件从你的本地仓库里清理掉。

如果要clone一个附带submodule的项目，submodule的文件不会自动随父项目clone出来（其实只会clone出 `.gitsubmodle` 这个描述文件），还需要执行如下命令取出submodule里的文件：

```shell
$ git submodule update --init --recursive
```

### Take an example

Generally

给出一个在父项目 `proj.git` 里添加submodule项目 `lib.git` 并使用的示例：

*(用户A)* 创建新的代码仓库：

```shell
mkdir proj
cd proj
git init
git add --all
```

*(用户A)* 添加pdlib作为submodule：

```shell
git submodule add git@github.com:lib.git
git commit -m "first commit with submodule"
git remote add origin git@github.com:proj.git
git push origin master
```

*(用户B)* 签出刚刚新建的代码仓库并使用：

```shell
git clone git@github.com:proj.git
cd foo
git submodule update --init --recursive
```

*(用户B)* 发现`lib.git`有修改，他把`proj.git`仓库的`lib.git`也同步到该版本：

```shell
cd lib
git pull
git status        # 此时如果lib.git有修改，就可以看到not staged commit
cd ..
git add lib
git commit -m "update lib.git"
git push origin master
```

*(用户C)* 更新`proj.git`仓库，同时也需要更新submodule：

```shell
git pull origin master
git status        # 记得执行git status，可以看到lib.git的改动
git submodule update
```

> 【注】这种情况下，需要清楚`lib.git`和`proj.git`实际就是两个独立的git仓库，针对`lib.git`的修改，需要在`lib`目录下commit。注意submodule*必须*是在master分支修改，如果`proj.git`在其他分支上开发，那么针对`lib`目录的修改需要先切回master分支。

*(用户D)* 想直接在`proj.git`仓库里修改`lib`目录的内容：

```shell
cd lib
git checkout master  # 注意修改lib需要在master分支上
edit xxx.txt
git add xxx.txt
git commit -m "update xxx.txt"
git push origin master
```

*(用户D)* 需要显式的把刚在`lib`目录上的修改添加到`proj.git`仓库里去：

```shell
cd proj
git status        # 每次在commit之前查看一下status是好习惯
git add lib
git commit -m "update lib.git"
git push origin master
```

## Merge request

如今很多gitlab项目都采取merge request方式来进行codereview，步骤如下：

1. 先在本地创建一个本地分支local_branch。

2. 改动local_branch你需要改动的代码。

3. 进入项目根目录下，运行如下代码，将local_branch推到远程分支。

   > ``` shell
   > $ git add .
   > $ git commit -a -m "first commit"
   > $ git push origin local_branch
   > ```

4. 在gitlab上面操作，进入项目下，点击merge request选项，然后选择之前推到远端的local_branch和要合并到哪个分支，比如合并到master上。

5. 点击merge request

## Pull request

pull request是针对github的，操作步骤同merge request类似。"Pull Request 是一种通知机制。你修改了他人的代码，将你的修改通知原来的作者，希望他合并你的修改，这就是 Pull Request。"

流程：

1. fork别人的代码，克隆到自己的仓库。
2. 在自己的仓库修改后的分支上，按下New pull request按钮。



