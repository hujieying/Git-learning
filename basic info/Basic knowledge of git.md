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
```
$ git status
```
**git diff** 顾名思义就是查看difference，提交到仓库之前，可以看看具体修改了哪些地方。
```
$ git diff readme.txt
```
**git checkout** 丢弃工作区的修改
```
$ git checkout -- readme.txt
```

### 版本回退
* HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令**git reset --hard commit_id**。
* 穿梭前，用**git log**可以查看提交历史，以便确定要回退到哪个版本。
* 要重返未来，用**git reflog**查看命令历史，以便确定要回到未来的哪个版本。

### 工作区和暂存区
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD

![git-1](https://github.com/hujieying/Git-learning/blob/git-ex/resource/git-1.jpeg)

前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。

![git-2](https://github.com/hujieying/Git-learning/blob/git-ex/resource/git-2.jpeg)  
![git-3](https://github.com/hujieying/Git-learning/blob/git-ex/resource/git-3.jpeg)

### 管理修改
GIT管理的是修改，而不是文件！
用git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别

### 撤销修改
**场景1**：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file:
```
$ git checkout -- readme.txt
```
命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况:

一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态。

**场景2**：当你不但改乱了工作区某个文件的内容，还添加（add）到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，把暂存区的撤销掉，就回到了场景1，第二步按场景1操作。
```
$ git reset HEAD readme.txt
```

**场景3**：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考*版本回退*一节，不过前提是没有推送到远程库。

### 删除文件













