## Git

* 什么是Git
* 什么是GitHub
* Git的由来
* 分布式和集中式
* Git和GitHub的使用
* 常见Git命令清单
* 工作区、暂存库和版本库

#### 什么是Git？

​	分布式版本控制工具

#### 什么是GitHub？

​	网站，GitHub是代码托管服务器

​	国内类似的网站 git.oschina.net coding.net等

#### Git的由来

很多人都知道，Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。

Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？

事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！

你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。

不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。

安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。

Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：

Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。

Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。

历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。

#### 集中式和分布式

**一、什么是集中式**

​        集中式开发：是将项目集中存放在中央服务器中，在工作的时候，大家只在自己电脑上操作，从同一个地方下载最新版本，然后开始工作，做完的工作再提交给中央服务器保存。这种方式需要联网，现在云开发就是这样的处理方式。

**缺点：**1.如果网络出现异常或者很卡，直接影响工作效率。如果是中央服务器挂了，那就集体喝茶去了。

​           2.还有一种情况，各自电脑中操作的所有软件工具，都存放在一个中央服务器上（现在流行叫云服务器），只需要用各自电脑登陆连接到云服务器上，（一般服务器都是用linux），比如用ps工具，大家其实用的是云服务器中的同一个ps 软件，在使用率高的情况下，ps会出现异常，当用ps筛选颜色的时候，已经混乱，无法正常选择颜色，这个情况是我在开发中遇到的。以前我们是每个人用各自安装的ps,但是在这样的环境下用的是同一个ps软件的时候就会有ｂｕｇ。

​            3.安全度不高，重要的东西都放在一个中央服务器中，如果被黑，那损失就大了。

 **优点：**1.减少了硬件和软件成本，硬件不用说了，现在流行盒子，一个小盒子只要连上中央服务器即可，以前都是一个个主机箱，那成本大多了。如果用到工具软件需要收费，只需买一套正版就OK了。

**二、什么是分布式**

​         分布式开发：只要提供一台电脑作为版本集中存的服务器放就够了，但这个服务器的作用仅仅是用来方便“交换”大家的修改，没有它也一样干活，只是交换修改不方便而已。而每一台电脑有各自独立的开发环境，不需要联网，本地直接运行，相对集中式安全系数高很多。

​     

#### Git和GitHub的使用

工作区-> 暂存区->本地分支->远程分支master->组织的源仓库

期间还可以通过``git status``去查看状态

1.添加

​	```git add ./A```

2.提交

​	```git commit -m '修改了xxx'```

3.推送

​	```git push```

4.GitHub通过pull request提交代码到源仓库

5.如果pull request 没有通过，你下次push依旧会保存在该pull request中

#### 常见Git命令清单

1、新建代码库

> ```
> # 在当前目录新建一个Git代码库
> $ git init
>
> # 新建一个目录，将其初始化为Git代码库
> $ git init [project-name]
>
> # 下载一个项目和它的整个代码历史
> $ git clone [url]
>
> ```

2、配置

Git的设置文件为`.gitconfig`，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

> ```
> # 显示当前的Git配置
> $ git config --list
>
> # 编辑Git配置文件
> $ git config -e [--global]
>
> # 设置提交代码时的用户信息
> $ git config [--global] user.name "[name]"
> $ git config [--global] user.email "[email address]"
>
> ```

3、增加/删除文件

> ```
> # 添加指定文件到暂存区
> $ git add [file1] [file2] ...
>
> # 添加指定目录到暂存区，包括子目录
> $ git add [dir]
>
> # 添加当前目录的所有文件到暂存区
> $ git add .
>
> # 添加每个变化前，都会要求确认
> # 对于同一个文件的多处变化，可以实现分次提交
> $ git add -p
>
> # 删除工作区文件，并且将这次删除放入暂存区
> $ git rm [file1] [file2] ...
>
> # 停止追踪指定文件，但该文件会保留在工作区
> $ git rm --cached [file]
>
> # 改名文件，并且将这个改名放入暂存区
> $ git mv [file-original] [file-renamed]
>
> ```

4、代码提交

> ```
> # 提交暂存区到仓库区
> $ git commit -m [message]
>
> # 提交暂存区的指定文件到仓库区
> $ git commit [file1] [file2] ... -m [message]
>
> # 提交工作区自上次commit之后的变化，直接到仓库区
> $ git commit -a
>
> # 提交时显示所有diff信息
> $ git commit -v
>
> # 使用一次新的commit，替代上一次提交
> # 如果代码没有任何新变化，则用来改写上一次commit的提交信息
> $ git commit --amend -m [message]
>
> # 重做上一次commit，并包括指定文件的新变化
> $ git commit --amend [file1] [file2] ...
>
> ```

5、分支

> ```
> # 列出所有本地分支
> $ git branch
>
> # 列出所有远程分支
> $ git branch -r
>
> # 列出所有本地分支和远程分支
> $ git branch -a
>
> # 新建一个分支，但依然停留在当前分支
> $ git branch [branch-name]
>
> # 新建一个分支，并切换到该分支
> $ git checkout -b [branch]
>
> # 新建一个分支，指向指定commit
> $ git branch [branch] [commit]
>
> # 新建一个分支，与指定的远程分支建立追踪关系
> $ git branch --track [branch] [remote-branch]
>
> # 切换到指定分支，并更新工作区
> $ git checkout [branch-name]
>
> # 切换到上一个分支
> $ git checkout -
>
> # 建立追踪关系，在现有分支与指定的远程分支之间
> $ git branch --set-upstream [branch] [remote-branch]
>
> # 合并指定分支到当前分支
> $ git merge [branch]
>
> # 选择一个commit，合并进当前分支
> $ git cherry-pick [commit]
>
> # 删除分支
> $ git branch -d [branch-name]
>
> # 删除远程分支
> $ git push origin --delete [branch-name]
> $ git branch -dr [remote/branch]
>
> ```

6、标签

> ```
> # 列出所有tag
> $ git tag
>
> # 新建一个tag在当前commit
> $ git tag [tag]
>
> # 新建一个tag在指定commit
> $ git tag [tag] [commit]
>
> # 删除本地tag
> $ git tag -d [tag]
>
> # 删除远程tag
> $ git push origin :refs/tags/[tagName]
>
> # 查看tag信息
> $ git show [tag]
>
> # 提交指定tag
> $ git push [remote] [tag]
>
> # 提交所有tag
> $ git push [remote] --tags
>
> # 新建一个分支，指向某个tag
> $ git checkout -b [branch] [tag]
>
> ```

7、查看信息

> ```
> # 显示有变更的文件
> $ git status
>
> # 显示当前分支的版本历史
> $ git log
>
> # 显示commit历史，以及每次commit发生变更的文件
> $ git log --stat
>
> # 搜索提交历史，根据关键词
> $ git log -S [keyword]
>
> # 显示某个commit之后的所有变动，每个commit占据一行
> $ git log [tag] HEAD --pretty=format:%s
>
> # 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
> $ git log [tag] HEAD --grep feature
>
> # 显示某个文件的版本历史，包括文件改名
> $ git log --follow [file]
> $ git whatchanged [file]
>
> # 显示指定文件相关的每一次diff
> $ git log -p [file]
>
> # 显示过去5次提交
> $ git log -5 --pretty --oneline
>
> # 显示所有提交过的用户，按提交次数排序
> $ git shortlog -sn
>
> # 显示指定文件是什么人在什么时间修改过
> $ git blame [file]
>
> # 显示暂存区和工作区的差异
> $ git diff
>
> # 显示暂存区和上一个commit的差异
> $ git diff --cached [file]
>
> # 显示工作区与当前分支最新commit之间的差异
> $ git diff HEAD
>
> # 显示两次提交之间的差异
> $ git diff [first-branch]...[second-branch]
>
> # 显示今天你写了多少行代码
> $ git diff --shortstat "@{0 day ago}"
>
> # 显示某次提交的元数据和内容变化
> $ git show [commit]
>
> # 显示某次提交发生变化的文件
> $ git show --name-only [commit]
>
> # 显示某次提交时，某个文件的内容
> $ git show [commit]:[filename]
>
> # 显示当前分支的最近几次提交
> $ git reflog
>
> ```

8、远程同步

> ```
> # 下载远程仓库的所有变动
> $ git fetch [remote]
>
> # 显示所有远程仓库
> $ git remote -v
>
> # 显示某个远程仓库的信息
> $ git remote show [remote]
>
> # 增加一个新的远程仓库，并命名
> $ git remote add [shortname] [url]
>
> # 取回远程仓库的变化，并与本地分支合并
> $ git pull [remote] [branch]
>
> # 上传本地指定分支到远程仓库
> $ git push [remote] [branch]
>
> # 强行推送当前分支到远程仓库，即使有冲突
> $ git push [remote] --force
>
> # 推送所有分支到远程仓库
> $ git push [remote] --all
>
> ```

9、撤销

> ```
> # 恢复暂存区的指定文件到工作区
> $ git checkout [file]
>
> # 恢复某个commit的指定文件到暂存区和工作区
> $ git checkout [commit] [file]
>
> # 恢复暂存区的所有文件到工作区
> $ git checkout .
>
> # 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
> $ git reset [file]
>
> # 重置暂存区与工作区，与上一次commit保持一致
> $ git reset --hard
>
> # 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
> $ git reset [commit]
>
> # 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
> $ git reset --hard [commit]
>
> # 重置当前HEAD为指定commit，但保持暂存区和工作区不变
> $ git reset --keep [commit]
>
> # 新建一个commit，用来撤销指定commit
> # 后者的所有变化都将被前者抵消，并且应用到当前分支
> $ git revert [commit]
>
> # 暂时将未提交的变化移除，稍后再移入
> $ git stash
> $ git stash pop
>
> ```

10、其他

> ```
> # 生成一个可供发布的压缩包
> $ git archive
> ```

#### 工作区、暂存库和版本库

**工作区**：我们会想当然的认为，当前仓库所在目录就是我们的工作区，其实这是不完全正确的。在当前仓库中，新增，更改，删除文件这些动作，都发生在工作区里面。

**暂存区**：英文叫stage, 或index。在版本库.git目录下，有一个index文件。它实际上就是一个包含文件索引的目录树，像是一个虚拟的工作区。在这个虚拟工作区的目录树中，记录了文件名、文件的状态信息（时间戳、文件长度等），文件的内容并不存储其中，而是保存在Git对象库（.git/objects）中，文件索引建立了文件和对象库中对象实体之间的对应。如果当前仓库，有文件更新，并且使用git add 命令，那么这些更新就会出现在暂存区中。

**版本库**：当前仓库下，如果没有任何的提交，那么版本库就是对应上次提交后的内容。下面这个图展示了工作区、版本库中的暂存区和版本库之间的关系。

