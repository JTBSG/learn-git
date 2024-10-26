参考视频 【【GeekHour】一小时Git教程】 https://www.bilibili.com/video/BV1HM411377j/?share_source=copy_web&vd_source=034a0873ab56af647173cb990449c4bc
# 1. Git介绍
Git是一个开源的分布式版本控制系统。\
github是一个面向开源及私有软件项目的仓库托管平台。
# 2. Git安装与配置
git官网： https://git-scm.com \
命令行中输入 `git -v` 可以查看git版本 \
点击鼠标右键选择 `git bash here` 打开git的linux格式终端操作界面 \ 
输入 `git config --global user.name "JTBSG"` 来配置用户名
输入 `git config --global user.email qiboxun@stu.hit.edu.cn` 来配置邮箱 \
输入 `git config --global credential.helper store` 来保存用户名和密码 \
可以通过输入 `git config --global --list` 来查看配置信息 
# 3. 创建仓库
创建仓库有两种方式，一种是在本地创建仓库，一种是采用 `git clone` 的方式来克隆一个仓库。 \
本地创建仓库：使用 `mkdir learn-git` 命令创建一个空文件夹，然后使用 `cd learn-git` 进入该文件夹中。 \
使用 `git init` 初始化仓库。初始化后的仓库主分支名称为master \
克隆远程仓库：直接使用 `git clone https://github.com/JTBSG/JTBSG_learn-git.git` 即可。 
# 4. Git的工作区域和文件状态
Git有三个工作区，分别是工作区、暂存区和本地仓库。\
工作区就是本地电脑上的目录。 \
暂存区用于保存即将提交到本地仓库的修改内容。 \
本地仓库即Git存储代码和版本信息的主要位置。 \

Git中的文件状态包括：未跟踪（Untrack）、未修改（Unmodified）、已修改（Modified）、已暂存（Staged）。
# 5. 将文件添加到仓库中
`git status` 查看当前仓库状态（当前仓库处于哪一个分支、当前仓库中有哪些文件、这些文件处于怎样的一个状态）。 \
`git add file1.txt` 将file1文件添加到暂存区，等待后续的提交操作。支持使用通配符和使用目录 \
`git commit -m "在这里添加提交信息"` 将暂存区中的文件提交到本地仓库中，不会提交工作区中的内容。 \
`git log` 用于查看提交记录，`git log --oneline`可以用于查看简洁的提交记录。
# 6. git reset 回退版本
`git reset --soft` 回退到某一个版本，同时保存工作区和暂存区中的文件。 \
`git reset --hard` 回退到某一个版本，同时删除工作区和暂存区中的文件，一般不推荐使用。 \
`git reset --mixed` 回退到某一个版本，同时删除暂存区中的内容，保存工作区中的内容。reset命令的默认参数即为mixed。
# 7. git diff查看差异
`git diff` 默认比较工作区和暂存区之间的差异内容。 \
`git diff --cached` 比较暂存区和本地仓库之间的差异。 \
`git dff 版本id1 版本id2` 比较两个版本之间的差异。 \
`git diff 分支1 分支2` 比较两个分支之间的差异。
# 8. git rm 删除文件
`git rm file1.txt` 命令可以将文件从工作区和暂存区中删除，然后再使用 `git commit` 命令进行提交。 \
`git rm --cached` 将文件从暂存区中删除，但是保留在工作区中。

# 9. .gitignore文件
.gitignore文件可以让我们忽略掉一些不应该被加入到版本库中的文件。
# 10. github
在windows中 `cd C:\Users\Administrator` 进入文件夹 \
`mkdir .shh` 创建.shh文件夹, `cd .shh` 进入文件夹 \
`ssh-keygen -t rsa -b 4096` 生成shh密钥，一路回车，生成的id_rsa.pub就是ssh的公钥，复制公钥文件中的内容，填入到github中即可。 \
如果不是第一次创建shh密钥，需要在ssh文件夹下使用 `touch config` 命令创建一个config文件，然后使用`vi config` 对该文件进行更改，在config文件中输入 \
`# github` \
`Host github.com` \
`HostName github.com` \
`PreferredAuthentications publickey` \
`IdentityFile ~/.shh/test` \
此处最后的test为新创建的shh密钥名称，按实际情况进行更改。 \
采用 `git push` 命令可以向远程仓库中推送更新内容。采用 `git pull` 命令可以从远程仓库中拉取更新内容。
# 11. 关联本地仓库和远程仓库
首先创建好本地仓库和远程仓库，进入本地仓库，使用以下命令 `git remote add origin 远程仓库的SSH` \
`git branch -M main` \
`git push -u origin main`
# 12. 在VSCode中使用Git
推荐在VSCode中使用Git，同时安装GitLens插件，体验要比PyCharm好很多。
# 13. 分支
分支是Git中一个非常重要的功能，可以将其看作是代码库中的不同版本，可以独立存在，并且有自己的提交记录，不同的开发工作可以在不同的分支上进行，最后再合并到主分支中即可。
`git branch` 命令可以查看当前仓库中的所有分支。 \
`git branch 分支名` 命令可以创建一个新的分支。 \
`git switch 分支名` 命令可以进行不同分支之间的切换。 \
`git merge 分支名` 命令可以将‘分支名’对应的分支合并到当前分支中，最后得到的是当前分支。 \
`git log --graph --oneline --decorate --all` 命令可以用于查看分支图。 \
`git branch -d 分支名` 命令可以用于删除已经完成合并的分支。 \
`git branch -D 分支名` 命令可以用于强制删除没有完成合并的分支。
# 14. 冲突解决
如果有两个分支对同一个文件进行了更改，并且产生了冲突，就需要手动解决冲突。在手动解决冲突后将更改添加到暂存区，然后进行提交。也可以使用 `git merge --abort` 命令终止此次合并操作。
# 15. 回退和rebase（变基）
任意分支上都可以进行rebase操作。 `git rebase main` 命令可以将其余分支上的提交记录变基到main分支上。


# 到这里你已经可以自己使用Git进行版本管理了，快来试一试吧！