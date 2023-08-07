### 1.Github

1.登录Github 之后，创建一个新的仓库；

2.填写仓库先关资料，一般只需要选一个合适的仓库名，然后确保仓库为 `public` 其他的保持默认就好；

![image-20230807163710010](https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230807163710010.png)







### 2.Token：需要手动创建

在github中，打开Settings
左侧菜单最下面点击Developer settings
选择Personal access tokens下的Tokens(classic)
点击右侧Generate new token按钮，选择classic
将生成的token复制到PicGo的设置里



### 3.PicGo

下载
下载PicGo v2.3.1，这是最新的release版本，选择合适的格式下载，下载完成后安装。

配置
打开PicGo，图床设置选择GitHub，有三个必须的配置

仓库名：填写为GitHub_username/repo_name
分支名：填写分支名，一般新建的repo默认分支为master或main，可以在repo的settings界面查看

将生成的token复制到PicGo的设置里

![image-20230807163249246](https://cdn.jsdelivr.net/gh/zhaowei1869/learning_pictures/code/explain/image-20230807163249246.png)

保存配置之后就可以上传图片了。打开上传区，选择一张图片，拖住上传。上传成功后会将URL复制到剪贴板。登陆Github看到图片已经成功上传了。

此时图片上传到了repo的根目录，如果想要上传至指定的目录，可以在PicGo设置界面设定存储路径，如设置为imgs/，图片便会上传至repo下的imgs目录。注意一定要加/，否则变得是图片名字，而不是图片存储的路径。

还有一个配置是自定义域名，这个在一开始配置时是不需要动的。如果后续需要使用CDN加快图片访问速度，可以去修改

### 参考：

1.https://blog.csdn.net/Darlinnn/article/details/130549217

2.[如何利用 Github 搭建自己的免费图床？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/353775844)

3.[Github图床搭建和使用（带CDN加速）_github 做图床有封号封仓库风险_XReformat的博客-CSDN博客](https://blog.csdn.net/u011291916/article/details/119194338)

4.[如何利用 Github 搭建自己的免费图床？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/347342082)