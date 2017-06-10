### Git与Github简单教程
    > Git: 是一个免费、开源、快速、高效的分布式版本控制系统！
    
    > GitHub: 是一个通过Git进行版本控制的软件源代码托管服务！

------


不好理解的话，可以按下面的简单解释理解！！！
    
    > Git: 一个可以查看文件修改记录和恢复历史文件状态的控制系统
    
    > GitHub: 远程仓库，可以把本地源码文件和git记录等文件上传到远程的仓库

---------------


#### 接下来我们要学会用 Git 和 GitHub

1. 安装 Git 

    由于我用的的是win10系统，所以暂说下win系统下的 Git 安装灰常简单，Google 下 Git，去官网下载安装包。然后一路下一步即可
    
    [Git下载地址](https://git-scm.com/)
    
    安装完成后，鼠标右键点击桌面多出一个选项 *Git Bash Here* ，接下来我们要用到这个Bash工具

--------
2. 初次使用需要设置用户名和用户邮箱

    打开bash工具,输入以下命令即可设置账户和邮箱

    ```
    $ git config --global user.name  "你的用户名"
    $ git config --global user.email  "你的邮箱"
    ```
    查看设置的用户名
    
    `$ git config --global user.name `
    
    查看设置的邮箱
    
    `$ git config --global user.email`

3. 注册一个GitHub账号

    注册地址[GitHub.com](https://github.com/)

4. 公钥设置
    执行命令
    `$ ssh-keygen -t rsa -b 4096 -C "自己的github邮箱" `
    一路回车，设置完成，在~/.ssh目录下产生了公钥id_rsa.pub和私钥 id_rsa
    复制公钥里面的内容，添加到GitHub上 SSH and GPG keys 设置
    
5. git init 指令初始化一个仓库

    `$ git init `

6. 找到一个合适的目录，创建一个blog文件夹，在blog里面创建一个 README.md文件

    ```
    $ mkdir blog
    $ cd blog
    $ touch README.md
    ```
    
7. git add . 指令将文件的更新添加到 暂存区
    
    `$ git add .`
    指令中 . 代表所有文件，也可以指定文件
    
8. git commit -m "提交说明"

    `$ git commit -m "first commit" `
     -m 必备，不然进入vim编辑模式
     如果不幸进入vim编辑文件状态，输入 :q 回车退出
     
9. 把本地仓库推送到GitHub上
在GitHub上，新建一个仓库，不带任何文件，新建成功后会提示如何操作。我选取下面的方式 
   ```
   $ git remote add origin git@github.com:zbhgit/blog.git
   $ git push -u origin master
   ```


10. 打开GitHub查看有没有上传成功


####  Git版本回退

* git status命令可以让我们时刻查看仓库当前的状态

* git diff 查看文件具体修改了什么内容

* git log 查看当前历史提交记录 `git log --pretty=oneline` 更美观的查看,如下
```
	f7e38985e89fbe0bb7c807fd9b6de31ff375c80d $.ajax
	be0c1f9e028c9fb04a7e21bcd866f487f2cb7ca1 jquery
	bb5978a730dad8aed8dd6323ed1bf6ef436a00d4 jQuery  1
```
当我们要回到指定版本时，使用下面的命令

`git reset --hard f7e389`

版本号是上面那SHA1计算出来的数字，我们只需取前6位即可

要查看历史提交记录 还有一个命令

```
$ git reflog
得到如下显示
f9fc997 HEAD@{20}: commit: learn event
2794353 HEAD@{21}: commit: learn Event
f778e3b HEAD@{22}: commit: 改错

```

* git checkout -- file  ： 撤销文件在工作区的所有修改。回到文件最后一次git commit或者git add时的状态

* git rm 删除文件，并且git commit，这样才能删除版本库中的文件



#### Git分支管理

 1. 创建分支
 `$ git checkout -b dev ` 
 命令中加上 -b 表示创建并切换分支，相当于下面两条命令

 ```
 	$ git branch dev // 创建分支
	$ git checkout dev // 选择分支
	$ git branch // 查看当前分支

 ```

 2. 合并分支 

 ```
 $ git merge dev  // 合并到master分支上

 ```

 3. 删除分支 

 ```
 $ git branch -d dev // 删除dev分支

 ```


 4. 解决冲突

使用git status 可以查看冲突的内容，git 用 <<<<<<< ======= >>>>>>> 标记出 不同分支的内容，我们修改后在提交


5. 存储和读取当前状态
```
$ git stash  //存储当前状态

$ git stash list // 查看存储状态列表 

$ git stash apply // 读取存储的状态

$ git stash drop // 删除存储的状态 

$ git stash pop // 读取并删除存储的状态

```


### 多人协作 

```
	$ git remote  //查看远程仓库信息

	$ git remote -v // 远程仓库详细信息

```

推送分支的选择 

```
$ git push origin master  // 推送到主分支
$ git push origin dev  // 推送到dev分支
```

从远程仓库抓取分支  

```
$ git pull 
```



