#### requests在电脑开启代理的情况下无法正常发送请求

和前面的第二个方法类似，通过设置代理，来进行访问。因为本地 开启梯子后，梯子默认会把整个系统的流量指向电脑的某个端口，然后再由梯子进行接收往外转发，所以我们只需要在Python的requests请求中设置代理，即可将脚本请求转向梯子。但是这个代理并非梯子节点的代理，而是系统的代理。

打开梯子后，在设置中找到对应的代理端口（通常是10809）然后加在代码中即可

```
proxy = {'http': '127.0.0.1:10809', 'https': '127.0.0.1:10809'}
r = requests.post(u, json=data, headers=headers, proxies=proxy)

proxy={"https": "https://122.148.122.111:90", "http": "http://122.148.122.111:90"} requests.get(url, proixies=proxy)


```

参考：[requests在电脑开启代理的情况下无法正常发送请求_big__apple的博客-CSDN博客](https://blog.csdn.net/big__banana/article/details/123873178#:~:text=因为本地,开启梯子后，梯子默认会把整个系统的流量指向电脑的某个端口，然后再由梯子进行接收往外转发，所以我们只需要在Python的requests请求中设置代理，即可将脚本请求转向梯子。)

#### 定时git自动push

一直在使用md文件进行知识总结和记录自己的一些感想，并选择了github作为托管平台。在这个过程中经常有一个问题困扰我：**有时会忘记同步最新的内容，导致换了一台电脑之后无法获取最新的内容；并且每次add，commit，push，着实浪费时间**。

所以在想，能不能让windows在特定条件下自动进行push？这样就可以减少push次数和避免遗忘push。

说干就干

##### 脚本

首先用一个脚本实现双击push。脚本内容很简单：

```bash
d:
cd D:\your_repo_dir  # 你的第一个工作站的仓库地址

if errorlevel 1 goto Fail
if errorlevel 0 goto Success

:Fail
e:
cd E:\your_repo_2 # 你的第二个工作站的仓库地址
goto End

:Success
echo 成功
goto End

:End

# 记录2条最近的更新时间
set m=%Date:~0,4%-%Date:~5,2%-%Date:~8,2%
set d=%time:~0,2%:%time:~3,2%:%time:~6,2%

set res=latest update time: %d% %m%
set /P OEM=<README.md

echo %res% > README.md
echo. >> README.md
echo %OEM%>> README.md


# git push
git status
git add . -A
git commit -m "update"
git push origin main
pause
```

脚本后缀改为`.bat`。这样双击bat文件，便可以实现push。

同时上述脚本实现了记录最近的仓库更新时间；同时可以兼容两个不同目录的工作地址。

新的问题来了，此时我仍然需要手动双击push，还是会存在上述所有的问题，问题并没有解决。有没有一种方法可以实现在电脑休眠或者锁定屏幕时实现后台自动push呢？

当然有，那就是使用windows自带的任务计划。

##### 任务计划

在win菜单栏里面有一个 `Windows 管理工具`文件夹，里面有一个叫做`任务计划程序`的应用程序，可以帮助我们完成这个工作。

在任务计划程序里面，进行以下操作：

1. 新建一个文件夹，用来存储自己的计划任务。
2. 右键刚创建的文件夹，选择创建任务；
3. 选择`常规`，在`名称`栏目里，给自己的任务起一个名字；
4. 选择`触发器`->`新建`，在`开始任务`选项里，选择`工作站锁定时`，点击`确定`；
5. 选择`操作`->`新建`，在`操作`选项里选择`启动程序`，在`程序或脚本`一栏的右侧点击`浏览`，选择自己的bat文件。选择后，点击`确定`。
6. 选择`条件`，取消`电源`相关的选项。这样在使用电源和不使用电源，均可以push;
7. 最后确定，大功告成。

触发器中的`工作站锁定时`，这个动作含义是电脑屏幕锁定时执行你的自定义脚本。电脑屏幕锁定时，电脑并没有停止工作，再次进入电脑桌面需要输入密码。

以上的任务计划可以实现在使用CTRL+L锁定屏幕时，git会自动push，是不是很简单！完美解放双手和时间，纵享丝滑！

------

来源：[高效的自动push解决方案—屏幕锁定时git自动push - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/596882845)
