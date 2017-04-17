### Git与Github简单教程
    > Git: 是一个免费、开源、快速、高效的分布式版本控制系统！
    
    > GitHub: 是一个通过Git进行版本控制的软件源代码托管服务！

------


不好理解的话，可以按下面的简单解释理解！！！
    
    > Git: 一个可以查看文件修改记录和恢复历史文件状态的控制系统
    
    > GitHub: 远程仓库，可以把本地源码文件和git记录等文件上传到远程的地方

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
     
9. 把本地仓库推送到GitHub上
   ```
   $ git remote add origin git@github.com:zbhgit/blog.git
   $ git push -u origin master
   ```

10. 打开GitHub查看有没有上传成功











优势

    * 速度快
    * 简单的设计
    * 允许上千个并行分支
    * 分布式

重要概念 

* 已提交 
* 已修改
* 已暂存

### 初次使用--起步

1. 初次使用需要设置姓名和邮箱
    
```
git config --global user.name "自己名称"
git config --global user.email "账户邮箱"

```
> 当不加名称 和邮箱时  是查看当前设置

```$xslt
git config --global user.name
git config --global user.email
```

2. 从github新建仓库，然后 clone到本地仓库

3. 本地初始化仓库 上传到github仓库

4. 分支操作





#### 基本指令
`$ git init`

`$ git add`

`$ git commit`

`$ git status`

`$ git diff`

`$ git log`

`$ git reset --hard  (commit id)or(HEAD-100)`

`$ git relog`

理解暂存区 stage（或者叫index）

`使用git add 提交到暂存区`

`$ git checkout -- file-name`


`$ git rm `



#### Github创建项目库

`$ git remote add origin https://github.com/zbhgit/learnGit.git`

`$ git push -u origin master
 `
 **提交一次后可以省去 -u 参数**
 
 ` $ git push origin master`
 
   `$ git clone git@github.com:zbhgit/git-learn`
   
   
   `$ git branch dev `
   
   `$ git checkour dev`
   
   `$ git branch`
   

   `$ git merge`
   
   `$ git branch -d dev`
   
   `$ git merge --no-f -m "merge width no-ff"`

`$ git checkout -b issue-101`


