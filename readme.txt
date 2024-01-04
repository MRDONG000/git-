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

回退
使用reset 版本回退
使用版本回退时Git必须知道回退到那个版本，其中HEAD表示当前版本，HEAD^表示上一个版本，HEAD^^表示上上一个版本以此类推