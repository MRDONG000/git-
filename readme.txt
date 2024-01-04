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