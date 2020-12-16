## git 安装完成后全局配置命令

> 注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

$ git config --global color.ui true #让Git显示颜色，会让命令输出看起来更醒目
```

## 建立本地Git仓库

> 建立个目录 在目录下执行`git init`命令,如果你使用Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文

```
$ mkdir gitstore

$ cd gitstore

$ git init
```

### Git使用常用命令

* git status 命令查看仓库当前状态
* git add file 文件提交到缓存区stage
  ![git 1.x](/assets/709594-20170831012943593-883223078.jpg)
  ![git 2.x](/assets/709594-20170831013019483-2138515257.jpg)
* git commit -m '提交内容说明' 提交到仓库分支
* git log 查看仓库版本日志
* git reset --hard HEAD^ 和 git reset --hard xxx 回退到某个版本
* git reflog 查看版本回退日志
* git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别
   linux版本导出差异文件
    git diff 2da595c daea1d6 --name-only | xargs zip update.zip 对比版本差异文件并导出zip包
   window版本
    右键Git Bash Here
    git archive -o update.zip HEAD $(git diff 70ad949... 7046619... --name-only)
* git checkout -- readme.txt 丢弃工作区修改
* git rm test.txt 加 git commit 删除文件
* git 导出指定版本
   git archive -o ../updated.zip HEAD $(git diff --name-only HEAD)
   git archive -o ../latest.zip NEW_COMMIT_ID_HERE $(git diff --name-only OLD_COMMIT_ID_HERE NEW_COMMIT_ID_HERE)
   git diff --name-only 76f4ccc65619f0cda40d7b2fa9f4bcf1cdf3934a e13374a780bbe40fb96e5a7d6ef3fd100c97984b > list.txt
   git archive -o ../latest.zip list.txt
   git archive -o latest.zip HEAD //导出最近修改

## 使用远程仓库GitHub

1. 创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id\_rsa和id\_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key，正常情况下一路回车就完成了

```
$ ssh-keygen -t rsa -C "xxx@email.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/xxx/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/xxx/.ssh/id_rsa.
Your public key has been saved in /c/Users/xxx/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:0rAkvPSFb1Qsno6dX4jm3Xz+bPB0EpDiMtmbA2BrqJg xxx@email.com
The key's randomart image is:
+---[RSA 2048]----+
|         ..  .   |
|   .  o...o o    |
|    +o++o* . .   |
|   ..=oBB o   .  |
| o ...++S* +   . |
|E .   .o* = . o o|
|       o o =   =.|
|        . o o ..o|
|             o.oo|
+----[SHA256]-----+
```

1. 登陆GitHub，打开“Account settings”，“SSH Keys”页面,点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id\_rsa.pub文件的内容

2. GitHub上新建个参考然后把本地仓库备份到GitHub上 在本地仓库的目录下执行命令

> 本地库和GitHub管连 http协议不允许所以下面的方式会报错 所以要采用https方式

```
$ git remote add origin git@github.com:simerlin/PythonLearn.git  ##http 方式 origin这个可以改成github

$ git remote add origin https://github.com/simerlin/PythonLearn.git ##https 方式
```

> 如果git仓库默认创建了文件 比如readMe.md 要先执行这个命令拉取下来

```
1. $ git pull --rebase origin master 

2. $ git remote -v 查看

3. $ git remote rm origin 删除关联

4. $ git push -u origin master 第一次同步本地库到github

5. $ git push origin master #以后可以直接用这个命令来推到Github上  

6. $ git push origin dev 推送dev 分支到远程仓库
```

> 参与一个开源项目可以现在github 上Fork 克隆到自己的仓库下 然后通过git clone 修改到自己仓库  
> 如果希望开源项目接收你的修改内容需要在GitHub上pull request 等待开源项目接受

## 从GitHub 上clone 个项目下拉

$ git clone [https://github.com/simerlin/webproject.git](https://github.com/simerlin/webproject.git)

## Git 分支创建

> git checkout命令加上-b参数表示创建并切换

```
$ git checkout -b dev
```

> 上面的的命令相等同于下面两步

```
$ git branch dev   #创建dev分支
$ git checkout dev #切换分支
```

> 列出所以分支

```
$ git branch
```

> 合并分支 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

```
$ git merge dev #dev 分支东西合并到当前分支默认是Fast forward模式

$ git merge --no-ff -m "merge with no-ff" dev
```

> 删除分支

```
$ git branch -d dev 
$ git branch -D dev # 强删
```

> 切换分支 除了checkout 推荐使用 switch 命令切换分支

$ git switch -c dev \#\#创建并切换到dev 分支

$ git switch master \#\#切换到主分支上

## Git 解决冲突

```
$ git status 查看冲突文件 然后解决提交
```

> 用带参数的git log也可以看到分支的合并情况

```
$ git log --graph --pretty=oneline --abbrev-commit

$ git log --graph ##命令可以看到分支合并图。
```

## bug分支处理

> 当你要修复一个代号101的bug的任务时，很自然地，你想创建一个分支issue-101来修复它，但是，等等，当前正在dev上进行的工作还没有提交而且这些还没完成不能提交的情况下，可以用stash命令保存工作场，等待后面恢复

```
$ git stash ##先保存工作场然后切一个bug分支

$ git checkout -b issue-101 ##切一个bug分支

$ git checkout master ##在issue-101上修完bug后切会master分支

$ git merge --no-ff -m "merged bug fix 101" issue-101 ## 修复好的合并到master上

$ git brach -d issue-101 ## 删除issue101 分支

$ git checkout dev # 回到dev 分支

$ git stash list #查看刚刚保存的工作场

$ git stash apply #只恢复工作场不删除stash内容

$ git stash apply stash@{0} #多次恢复工作场某个内容

$ git stash drop #删除stash 内容

$ git stash pop #恢复工作场并删除 stash内容

$ git cherry-pick xxx # 单独合并某个版本
```

## 远程仓库推送分支和抓取分支

```
$ git push origin master ##推送主分支到远程仓库

$ git push origin dev ## 推送dev分支到远程仓库

$ git clone https://github.com/simerlin/webproject.git

$ git branch #查看分支

$ git checkout -b dev origin/dev #取出远程仓库的dev分支

$ git pull #多人协作如果有人修改文件提交不了时候需要这个命令类似svn的update

$ git branch --set-upstream-to=origin/dev #如果git pull提示no tracking information，原因是没有指定本地dev分支与远程origin/dev分支的链接，根据提示，设置dev和origin/dev的链接,然后在执行pull命令
```

## rebase 变基

> rebase操作可以把本地未push的分叉提交历史整理成直线；  
> rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

```
$ git rebase

$ git log --graph --pretty=oneline --abbrev-commit
```

## 标签标记tag 发版本比较实用

```
$ git tag v1.0 #给当前版本打标签

$ git tag #列出所有标签
v1.0

$ git log --pretty=oneline --abbrev-commit # 日志中可以看到标签

361898b (HEAD -> master, tag: v1.0, origin/master) 删除readme
e29f4b9 添加readme
1819de9 添加readme
618acda Python Dict 和 set 数据类型
8684aa1 添加python项目目录
69e3dda Initial commit

$ git tag v0.1 69e3dda #给指定版本打标签

$ git show v1.0 ## 显示标签版本详情

commit 361898b6d20f797e88e65137db7cc7710251e04c (HEAD -> master, tag: v1.0, origin/master)
Author: xiaolinxu <925104693@qq.com>
Date:   Tue Oct 22 10:42:30 2019 +0800

    删除readme

diff --git a/Python/learn/readme.md b/Python/learn/readme.md
deleted file mode 100644
index 3cb9607..0000000
--- a/Python/learn/readme.md
+++ /dev/null
@@ -1,5 +0,0 @@
-# Python 基础学习项目目录 本地Git 管理
-  
-  > 2019-10-20 开始基础语法学习！
-  > fuck !!!
-

$ git tag -a v0.2 -m "v0.2 tag test" 8684aa1 ## 给指定版本打标签并写上标签注释
```

### 操作标签

```
$ git tag -d v0.2 #删除某个标签

  Deleted tag 'v0.2' (was 8e43d4f)

$ git push origin v0.1 #标签推送到远程仓库

  Total 0 (delta 0), reused 0 (delta 0)
  To https://github.com/simerlin/PythonLearn.git
  * [new tag]         v0.1 -> v0.1

$ git push origin --tags #全部标签推送到远程仓库

  Total 0 (delta 0), reused 0 (delta 0)
  To https://github.com/simerlin/PythonLearn.git
  * [new tag]         v1.0 -> v1.0

$ git tag -d v1.0 ##删除远程标签需要先删除本地标签       

  Deleted tag 'v1.0' (was 361898b)

$ git push origin :refs/tags/v1.0 ##然后执行这个命令删除远程标签

  To https://github.com/simerlin/PythonLearn.git
  - [deleted]         v1.0
```

## 忽略特殊文件 .gitignore

```
$ git add App.class

The following paths are ignored by one of your .gitignore files:
App.class
Use -f if you really want to add them.
```

> 可以用-f强制添加到Git：

```
$ git add -f App.class
```

> .gitignore写得有问题，需要找出来到底哪个规则写错了，可以用git check-ignore命令检查：

```
$ git check-ignore -v App.class

.gitignore:3:*.class    App.class
```



