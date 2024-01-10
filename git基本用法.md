
# git基本用法
## 一、git 的安装
进入[git官网](https://git-scm.com/)找到 downloads，然后根据自己的系统选择相对应的版本下载即可。
可以打开命令行使用指令 `git --version`来检查是否安装成功，如果返回版本信息即为安装成功。
## 二、git 的用法
以下包含一些 git 的基本命令操作，在 git 中，所有命令都是以 git 开头，例如 git init就是初始化一个 git 仓库。使用命令前，必须先切换到 git 的仓库目录，也就是先来到要作为仓库的文件夹中，然后从此目录中进入 git bash，方法为鼠标右键点击空白处，然后选择 git bash 即可打开 git bash 的命令行窗口。下面介绍一些基本命令的用法。
### 1、git status
此命令是用来查看当前仓库的状态的，里面会包含当前仓库的信息，比如 Untracked files 提示，表示仓库中有文件没有被追踪，并提示具体文件以及解决方法。如果仓库没有初始化，还会显示当前文件夹不是一个 git 仓库。此命令可以用来检查每个其他命令操作后仓库状态，方便我们理解。
### 2、git init
此命令是用来初始化一个仓库的，可以将一个文件夹初始化为空的仓库（即便文件夹中有文件也会被初始化为空仓库）。初始化之后使用 `git status` 命令将会提示 Untracked files，就是上文所说的。解决方法是使用 `git add` 命令。
### 3、git add
此命令用于将文件夹中的文件添加到 git 仓库中，添加后在使用 `git status` 命令就不会再报 Untracked files 提示，而是多出 Initial commmit 提示，即初始化提交。要注意的一点就是 `git add` 命令是并没有将文件加入 git 仓库，而是 加到了“临时缓冲区”，主要目的是防止我们错误提交。
### 4、git commit
此命令用来将信息提交给仓库，格式为 `git commit -m “first commit”`，其中 commit 为提交的意思，-m 表示提交信息，引号中的内容为提交信息。提交后再使用 `git status` 查看信息返回 nothing to commit，表示没有内容可以提交了。
### 5、git log
此命令用来查看提交日志，包括提交记录和提交记录的内容，包括Author提交作者和Date提交日期和提交信息。
### 6、git branch
此命令用来查看仓库中的分支情况。`\*` 后面跟的就是当前所处的分支。如果使用 `git branch a` 指令，就会创建一个新的分支名为 a。再输入 `git branch` 会看到 a 和 master两个分支。我们所处的依然为 master 主分支。
### 7、git checkout
此命令用来切换所处分支。如 `git checkout a` 会将所处分支切换为 a。还有一个快速创建新的分支并且切换的指令为 `git checkout -b b`，此命令会新创建一个分支名为 b 并将当前所处分支切换为 b。
### 8、git merge
此命令用于合并分支，先切换到 master 分支再使用 `git merge a`，就会将 a 分支合并到 master 中，使用时要注意合并时要考虑两分支是否有冲突。还要注意合并完之后分支不会消失，需要手动删除。
### 9、git branch -d 和 git branch -D
此命令用于删除分支，`git branch -d a` 会将 a 分支删除，如果 a 分支还未被合并则使用此命令无法将其删除，这是可用 `git branch -D a` 命令强制删除。
### 10、git tag

此命令用于给分支添加标签，如 `git tag v1.0` 会给当前分支加上 v1.0 的标签，可以使用 `git tag` 来查看标签记录。添加标签后，可直接使用标签来代替该分支，如 `git checkout v1.0` 即可切换到该标签下的状态。