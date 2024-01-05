Git is a version control system
Git is a free software

创建好文件夹，之后git bash里面初始化repository
git init
第一次使用git的时候要设置开发者签名
git config --global user.name 用户名
git config --global user.email 邮箱

git ststus 查看一下git当前状态
git commit -m "提交一条信息到git本地仓库中"   m是message的意思
git add a.js b.js .....   添加一个或多个文件
git add . 添加新文件和被修改的文件，不包括被删除文件
git add -u 添加被修改的文件和被删除的文件，不包括新文件
git add -A 添加所有变化文件

Git相关概念
工作区 （Working Directory）
就是你在电脑里能看到的文件夹目录，比如我的git练习文件夹就是一个工作区
暂存区（stage）
数据暂时存放的区域，可在工作区和版本库之间进行数据的友好交流
版本库（Repository）
存放已经提交的数据在工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库

在工作区修改好代码后，因为一些事情耽误了，导致没有及时添加到暂存区和提交到repository仓库中，这时要查看修改好的代码和仓库里的代码有什么区别可以使用
git diff 
指令来查看当前工作区的代码和仓库里面的代码有那些不同

在git中如果想删除文件，可以使用指令
rm 需要删除的文件
就可以删除了

如果要把工作区删除的文件，这一个删除操作添加到我们的暂存区中，可以使用
git rm 文件名
也可以使用 
git add -A 或 -U
来添加

如果不小心删除了一个不想删除的文件
方法一：
例如 不小心删除了a.js文件
我们可以不用提交到暂存区，使用恢复指令恢复删除了的文件
git restore 不小心删除的文件

方法二：
git checkout -- 文件名     撤销放弃修改指令
git checkout -- 很重要，一定要加--，不加--就变成了切换分支
新版本切换分支是 git restore ，这个操作是从git checkout里面分出来的，切换分支的操作是switch

readme.md 在工作区修改后还没有放到暂存区，这时撤销修改就回到和版本可一样的状态；
readme.md 已经从工作区添加到我们的暂存区，又作了修改，删除文件后，撤销修改就会返回到添加到暂存区后的状态

如果已经把修改后的文件添加到暂存区，可以使用git reset HEAD 文件名 将暂存区的修改撤销掉
也可以使用 git restore --staged 文件名 撤销暂存区的操作
git reset 命令既可以回退版本，也可以把暂存区修改回退到工作区。当我们用HEAD时，表示最新版本   

如果commit（提交）比较多，git log 的内容就会比较多。 在英文状态下按“q”,就可以退出git log状态。

git log 指令可以查看用户在当前仓库中所有commit提交日志
git log --pretty=oneline 参数可以让log日志一行输出

但是git log有一个缺点，当我们回退到之前的版本时输入git log只能看到当前和之前的版本，后面更新的就没办法看到了，
针对这个情况我们可以使用git reflog 就可以看到所有操作了

回退
使用reset 版本回退
使用版本回退时Git必须知道回退到那个版本，其中HEAD表示当前版本，HEAD^表示上一个版本，HEAD^^表示上上一个版本以此类推
如果要回退的版本较早，使用HEAD~数字的形式来进行回退

git reset --hard HEAD~2
git 可以通过指定版本号，回退到指定版本
版本号就是log日志中使用SHA1计算出类似于"1d9jsdv"的字符串
使用指定版本号回退版本时无需使用完整版本号，写前几位能跟其他版本号区分开就可以
git reset --hard 版本号（例如：537e0c10ef63eb47e4723fd8dd1839969a6ee129，一般取前六位就可以）

创建分支
git checkout -b dev   创建一个名字为dev的分支，-b表示创建并切换分支，相当于下面两条命令
1.git branch dev
2.git checkout dev

git 新版本使用switch进行分支切换
git switch dev 切换分支
git switch -c dev 创建并切换分支

git branch命令可以查看当前分支

如何合并分支
使用merge把dev分支的工作成果合并到master分支上
git merge dev
git merge命令用于合并指定分支到当前分支。合并后，再查看reademe.txt的内容，就可以看到，和dev分支的最新提交是完全一样的
合并完成后甚至可以删除dev分支，删除dev分支就是把dev指针给删除掉，删掉后，我们就只剩下了一条master分支

删除分支
git branch -d dev(分支名)

分支合并是可能有冲突的，那如何解决冲突呢？
解决冲突
介绍：在真实开发中合并分支往往也不是一份风顺的，当git无法自动合并分支时，就必须首先先解决冲突，冲突解决后再提交，合并完成
在工作区手动去操作不同的地方，解决完问题后，先提交到暂存区然后提交到仓库中，然后再次合并

使用git log --graph 命令可以看到分支合并图

分支策略
在实际开发中，我们应该按照几个基本原则进行分支管理：
1.master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活
2.干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master分支上，在master分支上发布1.0版本
3.团队开发中我们每个人都在dev分支上干活，每个人都有自己的分支，时不时的往dev分支上合并就可以了


使用GitHub
注册账户以及创建仓库
1.配置：首先要在本地配置一个密钥，只有通过密钥才可以在github的仓库中去修改，别人只能查看和下载
打开cmd命令面板，里面输入命令 ssh-keygen -t rsa -C "邮箱"，例如ssh-keygen -t rsa -C "783508268@qq.com"

成功后可以在用户主目录里找到ssh目录，里面有id_rsa和id_rsa.pub两个文件，id_rsa是SSH Key的私钥，不能泄露出去，id_rsa.pub是SSH Key的公钥
可以放心告诉任何人

如何在github上配置？
步骤
1.点击头像，点击设置，选择SSH and GPG keys
2.点击SSH keys 去newSSH key，其中title可以随便写，代表访问仓库的电脑机器，接着在Key中把id_rsa.pub中的代码粘贴过去然后保存就好了

配置好后创建仓库，就可以使用了
首先配置好了SSH协议后，就可以直接使用我们的电脑通过SSH协议访问github上的仓库
通过git面板，
1.通过SSH协议访问github仓库
输入：git remote add origin git@github.com:MRDONG000/git-.git
意译为：将远程仓库的分支origin和本地仓库进行一个匹配
2.通过HTTP协议访问github仓库
输入：git remote add origin https://github.com/MRDONG000/git-.git

接着如何把项目上传到github远程仓库上，可以使用git push -u origin（远程仓库分支） master(本地仓库分支)命令
git push -u origin main（本地仓库的分支名，一般本地仓库的分支名叫master）
意义：将当前分支仓库的项目发送到远程仓库分支origin中，一般远程仓库origin开发的主分支是main
所以可以使用
git push -u origin main:master 命令将本地项目发送到远程仓库origin分支下的main分支中

如何在github上下载别人的项目
可以git clone + Code里面的SSH或者HTTP命令，就可以了
例如:git clone git@github.com:MRDONG000/git-.git



