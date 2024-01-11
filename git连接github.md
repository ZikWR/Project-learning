# git 连接 github
## 一、创建仓库
进入[github官网](https://github.com/)登录自己的账号（没有账号的注册一个），进入个人主页后点击右上角加号选择 New repository 创建新仓库，填写完相关信息点击 create repository 即可创建新仓库。
## 二、利用 SSH 绑定 git 与 github
首先需要安装 SSH，来到我们本地仓库打开 git bash，输入命令`ssh`就可以安装 SSH 了。然后输入命令`ssh-keygen -t rsa`，表示指定 RSA 算法生成密钥，然后按三次回车键，期间无需输入任何字符，之后就会生成两个文件，分别为 id_rsa 和 id_rsa.pub，分别为密钥和公钥，它们都为隐藏文件，在 windows 系统中默认会放在C盘中user里名为.ssh的文件夹中。
之后，我们要把 SSH key 添加到 github 的个人账户中。进入个人主页，点击右上角自己头像旁边的倒三角，找到 settings 选项，然后选择 SSH and GPG keys，点击 New SSH key，然后只需将公钥 id_rsa.pub 的内容粘贴到 key 处，再点击 Add SSH key 就添加上了。可以回到本地仓库打开 git bash 输入`ssh -T git@github.com`进行验证。
到此，我们就完成了 git 与 github 的绑定
## 三、通过 git 提交代码到 github
这里要用到两个命令 push 和 pull 来提交和拉取代码
push 命令格式为`git push origin master`，其中master为分支名，此命令的意思为将本地的代码推到远程仓库。
pull 命令格式为`git pull origin master`，此命令的意思为将远程仓库中的代码拉到本地仓库中。
提交代码有两种情况，第一种是本地没有 git 仓库，第二种是本地有 git仓库，并且已经进行了多次 commit 操作。
对于第一种情况，我们可以直接使用 clone 命令将远程仓库 clone 到本地。使用方法为在你要建立仓库的位置打开 git bash，并且复制需要 clone 的仓库的网址，使用命令`git clone <网址>`即可。然后将你要提交的代码文件复制到本地仓库里，使用上文提到的 add 和 commit 命令提交到本地仓库，然后使用 push 命令`git push origin master`，第一次向远程仓库提交时需要输入账号密码进行验证，成功后，刷新github页面，即可看到刚刚提交的代码文件。
对于第二种情况，先进入本地仓库的 git bash，并用 init 命令初始化操作，然后使用`git remote add origin <网址>`命令，即可关联远程仓库。再使用 pull 命令同步远程与本地仓库，最后使用 push 命令推到远程仓库即可（push 之前要将需提交的代码 add 和 commit）。
