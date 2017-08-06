# 基础知识点

## 创建版本库
版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

首先，选择一个合适的地方，创建一个空目录：
```
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
```
pwd命令用于显示当前目录。在我的Mac上，这个仓库位于/Users/hujieying/learngit。

第二步，通过git init命令把这个目录变成Git可以管理的仓库：
```
$ git init
Initialized empty Git repository in /Users/hujieying/learngit/.git/
```

把一个文件放到Git仓库只需要两步
第一步，用命令git add告诉Git，把文件添加到仓库：
```
$ git add readme.txt
```

第二步，用命令git commit告诉Git，把文件提交到仓库：
```
$ git commit -m "wrote a readme file"
[master (root-commit) cb926e7] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

### 小结
初始化一个Git仓库，使用**git init**命令。

添加文件到Git仓库，分两步：

第一步，使用命令**git add (file)**，注意，可反复多次使用，添加多个文件;
  
第二步，使用命令**git commit -m "xxxx"**，-m后面的引号中填写本次提交是干嘛的，方便后续追溯，完成。



## 时光穿梭
**git status** 命令可以让我们时刻掌握仓库当前的状态
**git diff** 顾名思义就是查看difference，提交到仓库之前，可以看看具体修改了哪些地方。

### 版本回退
* HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
* 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
* 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

### 工作区和暂存区
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD

![工作区和版本库](Git-learning/resource/git-工作区和版本库.jpeg)























