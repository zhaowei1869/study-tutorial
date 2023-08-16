





- 要随时掌握工作区的状态，使用`git status`命令。
- 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容



知道了对`readme.txt`作了什么修改后，再把它提交到仓库就放心多了，提交修改和提交新文件是一样的两步，第一步是`git add`：

```
git add readme.txt
```

同样没有任何输出。在执行第二步`git commit`之前，我们再运行`git status`看看当前仓库的状态：

```
git status

On branch master
Changes to be committed:
(use "git reset HEAD <file>..." to unstage)
modified:   readme.txt
```



`git status`告诉我们，将要被提交的修改包括`readme.txt`，下一步，就可以放心地提交了：

```
git commit -m "add distributed"

[master e475afc] add distributed
1 file changed, 1 insertion(+), 1 deletion(-)
```

<img src="https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230808144001654.png" alt="image-20230808144001654" style="zoom:50%;" />

<img src="https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230808144038387.png" alt="image-20230808144038387" style="zoom:50%;" />

<img src="https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230808144057631.png" alt="image-20230808144057631" style="zoom:50%;" />







<img src="https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230808144134799.png" alt="image-20230808144134799" style="zoom:67%;" />





IDEA中集成Git

1.新建项目，绑定Git

2.修改文件，使用IDEA操作文件

3.提交测试



## Git 基本操作

------

Git 的工作就是创建和保存你项目的快照及与之后的快照进行对比。

本章将对有关创建与提交你的项目快照的命令作介绍。

Git 常用的是以下 6 个命令：**git clone**、**git push**、**git add** 、**git commit**、**git checkout**、**git pull**，后面我们会详细介绍。

<img src="https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230808144642398.png" alt="image-20230808144642398" style="zoom:67%;" />

**说明：**

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库

一个简单的操作步骤：

```
$ git init    
$ git add .    
$ git commit  
```

- git init - 初始化仓库。
- git add . - 添加文件到暂存区。
- git commit - 将暂存区内容添加到仓库中。

### 创建仓库命令

下表列出了 git 创建仓库的命令：

| 命令        | 说明                                   |
| :---------- | :------------------------------------- |
| `git init`  | 初始化仓库                             |
| `git clone` | 拷贝一份远程仓库，也就是下载一个项目。 |

------

### 提交与修改

Git 的工作就是创建和保存你的项目的快照及与之后的快照进行对比。

下表列出了有关创建与提交你的项目的快照的命令：

| 命令         | 说明                                     |
| :----------- | :--------------------------------------- |
| `git add`    | 添加文件到暂存区                         |
| `git status` | 查看仓库当前的状态，显示有变更的文件。   |
| `git diff`   | 比较文件的不同，即暂存区和工作区的差异。 |
| `git commit` | 提交暂存区到本地仓库。                   |
| `git reset`  | 回退版本。                               |
| `git rm`     | 将文件从暂存区和工作区中删除。           |
| `git mv`     | 移动或重命名工作区文件。                 |

### 提交日志

| 命令               | 说明                                 |
| :----------------- | :----------------------------------- |
| `git log`          | 查看历史提交记录                     |
| `git blame <file>` | 以列表形式查看指定文件的历史修改记录 |

### 远程操作

| 命令         | 说明               |
| :----------- | :----------------- |
| `git remote` | 远程仓库操作       |
| `git fetch`  | 从远程获取代码库   |
| `git pull`   | 下载远程代码并合并 |
| `git push`   | 上传远程代码并合并 |



## Git上传本地文件步骤

------

#### 1、“git init”初始化項目文件

（先进入项目文件夹）通过命令 “git init” 把这个目录变成git可以管理的仓库

```kotlin
git init
```



#### 2、“git add .”把文件添加到版本库中，

使用命令 “git add .”添加到暂存区里面去，不要忘记后面的小数点“.”，意为添加文件夹下的所有文件

```csharp
git add .
```



#### 3、“git commit -m”提交到仓库

用命令 “git commit -m” 告诉Git，把文件提交到仓库。引号内为提交说明

```bash
git commit -m '提交文件'
```



#### 4、关联到远程库 

“git remote add origin 你的远程库地址”。添加后，远程库的名字就是`origin`，这是Git默认的叫法，也可以改成别的，但是`origin`这个名字一看就知道是远程库。

```csharp
git remote add origin 你的远程库地址
例如:git remote add origin https://github.com/qiyiou25/qiu.git
```



#### 5、获取远程库与本地同步合并

（如果远程库不为空必须做这一步，否则后面的提交会失败）

```undefined
git pull --rebase origin master
<<<<<<< HEAD

git pull = git fetch + git merge
git pull --rebase = git fetch + git rebase
=======
>>>>>>> 879c6db48220e6e336d211d9a1f7cdb7d64c3d41
```



#### 6、把本地库的内容推送到远程，

使用 git push命令，实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码，验证通过后即开始上传。

把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。

由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

```undefined
git push -u origin master
```



推送成功后，可以立刻在GitHub/Gitee页面中看到远程库的内容已经和本地一模一样。从现在起，只要本地作了提交，就可以通过命令：

```
$ git push origin master
```

#### 7、状态查询命令

```undefined
git status
```

> 小结：
>
> 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；
>
> 关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；
>
> 关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；
>
> 此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；
>
> 分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！
>
> 要养成上班先git pull，下班git push的习惯，才能保证在最终git push的时候本地commit历史和远程commit历史是一致的





------



#### 删除已有的GitHub/Gitee远程库：

```
git remote rm origin
```



#### 再关联Gitee的远程库

（注意路径中需要填写正确的用户名）：

```
git remote add origin git@gitee.com:liaoxuefeng/learngit.git
```

此时，我们再查看远程库信息：

```
git remote -v
origin  https://gitee.com/zhaowei1869/group-decision-making-paper.git (fetch)
origin  https://gitee.com/zhaowei1869/group-decision-making-paper.git (push)
```

现在可以看到，origin已经被关联到Gitee的远程库了。通过`git push`命令就可以把本地库推送到Gitee上。

有的小伙伴又要问了，一个本地库能不能既关联GitHub，又关联Gitee呢？

答案是肯定的，因为git本身是分布式版本控制系统，可以同步到另外一个远程库，当然也可以同步到另外两个远程库。

使用多个远程库时，我们要注意，git给远程库起的默认名称是`origin`，如果有多个远程库，我们需要用不同的名称来标识不同的远程库。

仍然以`learngit`本地库为例，我们先删除已关联的名为`origin`的远程库：

```
git remote rm origin
```

然后，先关联GitHub的远程库：

```
git remote add github git@github.com:michaelliao/learngit.git
```

注意，远程库的名称叫`github`，不叫`origin`了。

接着，再关联Gitee的远程库：

```
git remote add gitee git@gitee.com:liaoxuefeng/learngit.git
```

同样注意，远程库的名称叫`gitee`，不叫`origin`。

现在，我们用`git remote -v`查看远程库信息，可以看到两个远程库：

```
git remote -v
gitee	git@gitee.com:liaoxuefeng/learngit.git (fetch)
gitee	git@gitee.com:liaoxuefeng/learngit.git (push)
github	git@github.com:michaelliao/learngit.git (fetch)
github	git@github.com:michaelliao/learngit.git (push)
```

如果要推送到GitHub，使用命令：

```
git push github master
```

如果要推送到Gitee，使用命令：

```
git push gitee master
```

这样一来，我们的本地库就可以同时与多个远程库互相同步：

```ascii
┌─────────┐ ┌─────────┐
│ GitHub  │ │  Gitee  │
└─────────┘ └─────────┘
     ▲           ▲
     └─────┬─────┘
           │
    ┌─────────────┐
    │ Local Repo  │
    └─────────────┘
```





### 把文件添加到版本库

首先这里再明确一下，所有的版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等，Git也不例外。版本控制系统可以告诉你每次的改动，比如在第5行加了一个单词“Linux”，在第8行删了一个单词“Windows”。而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道。

不幸的是，Microsoft的Word格式是二进制格式，因此，版本控制系统是没法跟踪Word文件的改动的，前面我们举的例子只是为了演示，如果要真正使用版本控制系统，就要以纯文本方式编写文件。

因为文本是有编码的，比如中文有常用的GBK编码，日文有Shift_JIS编码，如果没有历史遗留问题，强烈建议使用标准的UTF-8编码，所有语言使用同一种编码，既没有冲突，又被所有平台所支持。

使用Windows的童鞋要特别注意：

千万不要使用Windows自带的**记事本**编辑任何文本文件。原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们自作聪明地在每个文件开头添加了0xefbbbf（十六进制）的字符，你会遇到很多不可思议的问题，比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等，都是由记事本的弱智行为带来的。建议你下载[Visual Studio Code](https://code.visualstudio.com/)代替记事本，不但功能强大，而且免费！



## git add .，git add -A，git add -u，git add * 的区别与联系

这几个命令在不同版本的 Git 中稍有差异。

### 对于 Git Version 1.x：

1. `git add .`：会将当前工作区中当前目录(包括子目录)下的所有新文件和对已有文件的改动提交至暂存区，但不包括被删除的文件。
2. `git add -u`：`git add --update` 的简写形式，它只会监控当前整个工作区中之前已被 `add` 的文件，即已被跟踪(tracked)的文件，也就是只会将当前整个工作区中被修改和被删除的文件提交至暂存区。而新文件因为未被跟踪(untracked)，所以不会被提交至暂存区。
3. `git add -A`：`git add --all` 的简写形式，它会将当前整个工作区中所有的文件改动提交至暂存区，包括新增、修改和被删除的文件，不受当前所在目录限制。

注意：你会看到有些文章说 `git add -A` 属于 `git add .` 和 `git add -u` 功能的合集，这是不对的。因为 `git add .` 只会提交当前目录(包括子目录)下的新文件和对已有文件的改动，而 `git add -A` 不受当前目录限制。也就是说，`git add .` 和 `git add -u` 功能的合集只能属于 `git add -A` 功能的子集。

**总结详见下图：**

| Git Version 1.x | 新文件 | 被修改的文件 | 被删除的文件 | 是否受当前所在目录限制 | 说明                                                         |
| --------------- | ------ | ------------ | ------------ | ---------------------- | ------------------------------------------------------------ |
| git add -A.     | ✅      | ✅            | ✅            | ❌                      | 将当前整个工作区中所有的文件改动提交至暂存区，包括新增、修改和被删除的文件，不受当前所在目录限制 |
| git add .       | ✅      | ✅            | ❌            | ✅                      | 将当前工作区中当前目录(包括子目录)下的所有新文件和对已有文件的改动提交至暂存区，但不包括被删除的文件 |
| git add -u.     | ❌      | ✅            | ✅            | ❌                      | 将当前整个工作区中被修改和被删除的文件提交至暂存区。而新文件因为未被跟踪(untracked)，所以不会被提交至暂存区 |

### 对于 Git Version 2.x：

在 Git --version 2.x 中对 `git add .` 的功能做了改动，`git add .` 会提交当前工作区中当前目录(包括子目录)下所有的文件改动，不像在 Git --version 1.x 时那样不包括被删除的文件。

Git Version 2.x 中如果想在使用 `git add .` 时不提交被删除的文件，可以使用 `git add --ignore-removal` 加上匹配符 `.`，即 `git add --ignore-removal .`。

`git add --ignore-removal` 后的匹配符是可以更换的(但不能缺省)，例如 `git add --ignore-removal -A` 可以实现在 `git add -A` 时不提交被删除的文件。

有些文章说在 Git --version 2.x 中 `git add .` 和 `git add -A` 的功能变得完全相同，这是不对的。因为我们之前提到过，`git add .` 提交的文件改动受当前所在目录限制，它只会提交当前工作区中当前目录(包括子目录)下的文件改动，而 `git add -A` 不受当前所在目录的限制，提交的是当前整个工作区中所有的文件改动。

#### git add *

`git add *` 表示添加当前目录(包括子目录)下的所有文件改动，但不包括文件名以 `.` 符号开头的文件的改动。这是 Shell 命令，git 只是接收文件列表。而 `git add .` 的功能与 `git add *` 基本相同，只是 `git add .` 会将文件名以 `.` 符号开头的文件的改动也提交至暂存区。

**总结详见下图：**

| Git Version 2.x | 新文件 | 被修改的文件 | 被删除的文件 | 是否受当前所在目录限制 | 说明                                                         |
| --------------- | ------ | ------------ | ------------ | ---------------------- | ------------------------------------------------------------ |
| git add -A      | ✅      | ✅            | ✅            | ❌                      | 将当前整个工作区中所有的文件改动提交至暂存区，包括新增、修改和被删除的文件，不受当前所在目录限制 |
| git add .       | ✅      | ✅            | ✅            | ✅                      | 将当前工作区中当前目录(包括子目录)下的所有的文件改动提交至暂存区，包括新增、修改和被删除的文件 |
| git add -u.     | ❌      | ✅            | ✅            | ❌                      | 将当前整个工作区中被修改和被删除的文件提交至暂存区。而新文件因为未被跟踪(untracked)，所以不会被提交至暂存区 |
| git add *       | ✅      | ✅            | ✅            | ✅                      | 将当前工作区中当前目录(包括子目录)下的所有的文件改动提交至暂存区，包括新增、修改和被删除的文件，但不包括文件名以 `.` 符号开头的文件的改动 |

------

作者：LeviDing
链接：https://juejin.cn/post/7053831273277554696
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



## 解决Git中出现 “LF will be replaced by CRLF“ 警告

Windows中使用CRLF标识一行的结束，而在Linux/UNIX系统中只使用LF标识一行的结束。CRLF即Carriage-Return Line-Feed的缩写。通常情况下，Git库不会自动修改文件内容，但是默认会将入库的文件的行尾符设置为LF，会将检出的文件的行尾符设置为CRLF。在执行如下操作时出现如下警告：


说明：工作目录中的mywebdav.conf文件的行尾是LF，但是这里在即将入Git库之前，却将LF转换为CRLF。所以给出警告。该警告无伤大雅，因为在Git库中的该文件仍然以LF为行尾。
中的设置相关。

在工作目录中，我们可以通过设置eol属性控制一个文件的行尾为CRLF或LF。我们也可以通过设置core.eol属性控制当前Git库中的所有文件的行尾为CRLF或LF。我们还可以设置core.autocrlf属性以覆盖core.eol属性的设置。如果要设置工作目录中的文件的行尾总是CRLF，而Git库中的文件的行尾总是LF，可以core.autocrlf=true。

默认core.autocrlf属性设置如下:

git config --global --get core.autocrlf
true
1
2
设置core.autocrlf属性为false，去除警告：

git config --global core.autocrlf false
<<<<<<< HEAD

## 实操

![image-20230807164823982](https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230807164823982.png)![image-20230808143211725](https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230808143211725.png)

## 参考：

------

链接：https://blog.csdn.net/linzeliang1222/article/details/108571209

[使用Gitee - 廖雪峰的官方网站 (liaoxuefeng.com)](https://www.liaoxuefeng.com/wiki/896043488029600/1163625339727712)

链接：https://www.jianshu.com/p/5f4169e50835
