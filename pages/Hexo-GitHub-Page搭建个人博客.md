---
title: Hexo+GitHub Page搭建个人博客
date: 2020-10-13 03:45:36
tags: [Hexo,GitHub Page,博客]
categories: 
- 博客
- Hexo
description: 使用免费的Github Page和Hexo搭建个人博客，选用next主题
---

# 记一次使用Github Page和hexo搭建个人博客

我用到的工具：
- PicGo:图床管理,[github下载](https://github.com/Molunerfinn/PicGo/releases)
- ShareX:截图,steam免费下载
- ## 环境与安装
  
  1. 安装好node和git，并注册号github账号
    | Git | Nodejs| GitHub |
    | --- | ---| --- |
    | [Git下载](https://git-scm.com/downloads) | [Nodejs下载](https://nodejs.org/zh-cn/) | [GitHub注册](https://github.com/)|
  
  2. 检查版本
  
    ```shell
    git version
    node -v
    npm -v
    ```
  
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/git-v.png)
  
  3. 安装hexo
  
    创建一个文件夹，文件夹内右键Git Bash Here 执行:``npm install -g hexo-cli``
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_9CshgcY4DP.png)
    安装好后，执行以下命令，在新文件夹创建所需文件
  
    ```shell
    hexo init myBlog
    cd myBlog
    npm install
   ```
  
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_oN3xD1u1mc.png)
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_rTyIO2jyeD.png)
  
    安装好后，myBlog文件夹的目录如下:
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/msedge_4e0qlhEige.png)
  
    继续执行``hexo generate``
  
  4. 查看hexo运行效果
  
    git bash终端执行``hexo s``命令
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_3rQ6XYra1x.png)
    最后在浏览器中输入``http://localhost:4000``回车就可以预览效果了
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/msedge_vrnBHdSBuX.png)
    以上是我修改后的主题的预览效果，使用了[next主题](https://github.com/theme-next/hexo-theme-next)
  
    接下来就是部署到github了
  
  5. 注册github
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/GitHub.png)
    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/Join-GitHub.png)
    注册好，邮箱验证好后，就可以登录了
  
    然后新建一个仓库
  
    <b style="color:#FF0000">ps:只能使用一个同名仓库托管一个静态站点</b>
	-
	- 由于我已经创建好了，就网上找了张图
	    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/msedge_iPq2wb9mnr.png)
	  
	    下面是我的仓库设置
	    ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/Options1.png)
	  
	    设置settings里面选择GitHub Page主题
	  
	    创建好后，就可以访问http://你的用户名.github.io查看初始效果了
	  
	  6. 配置ssh
	  
	    * 监测是否有已经存在的SSH keys:
	        
	        git bash 终端执行:`` ls -al ~/.ssh ``
	  
	        如果有SSH keys: 就会看到如下文件 id_rsa    id_rsa.pub
	        ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_ZsX7TQaxMJ.png)
	        (除了我自己生成的这种,官方教程里说,SSH keys也有可能是以下几种文件:
	- id_dsa.pub
	- id_ecdsa.pub
	- id_ed25519.pub
	          )
	      * 如果没有的话,就生成一个SSH keys:
	  
	          先执行以下命令配置本地账户:
	  
	          ```shell
	          git config --global user.name "用户名"
	          git config --global user.email "邮箱地址"
	          ```
	  
	          ``ssh-keygen -t rsa -C "上面的游戏"``
	  
	          然后会出现:
	  
	          ```shell
	          Generating public/private rsa key pair.
	          Enter file in which to save the key (/Users/you/.ssh/id_rsa): 
	          ```
	  
	          就是让你输入SSH keys要保存在哪里,一般不用改,就直接回车就好了.
	  
	          然后会出现:
	  
	          ```shell
	          Enter passphrase (empty for no passphrase): [Type a passphrase] 
	          # Enter same passphrase again: [Type passphrase again] 
	          ```
	          冒号后面输入一个密码,这个密码后面会用到,所以要记住!
	  
	          创建成功后,他会提示你SSH keys保存在哪里:
	  
	          ```shell
	          Your identification has been saved in /Users/you/.ssh/id_rsa.
	          # Your public key has been saved in /Users/you/.ssh/id_rsa.pub.
	          # The key fingerprint is:
	          # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com
	          ```
	  
	          如图:
	          ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/ssh_p1.png)
	  
	      * 找到SSH keys:
	  
	          根据上一步里告诉你的路径,找到保存SSH keys的地方,我的是在 C:\Users\zqzes\.ssh
	  
	          其中 id_rsa.pub 就是SSH keys 如果为了防止以后找不到,可以把他们自己另存到其它地方
	  
	      * 为github仓库添加SSH keys
	  
	          打开上面创建的仓库,点击'Settings',再左侧的'Deploy keys':
	          ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/Options21.png)
	  
	          点击'Add deploy key'
	  
	          然后把上面创建的id_rsa.pub里的内容复制到Key里去,Title部分随便填. 点击'Add key'
	  
	          添加的过程中,还要再输入一次github的密码
	  
	      * 测试连接
	  
	          回到git bash执行``ssh -T git@github.com``
	          ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_7Juqz6PmpM.png)
	          如上图，一些奇怪的提示，最后问你yes/no，输入yes就好
	          然后提示你输入密码，如下
	  
	          ```shell
	          Enter passphrase for key '/c/Users/zqzes/.ssh/id_rsa':
	          ```
	          最后它提示你:
	  
	          ```shell
	          Hi, 用户名/用户名.github.io! You've successfully authenticated, but GitHub does notprovide shell access.
	          ```
	      这样就ok了
	  
	  7. 配置yml准备发布
	      myBlog内有个文件叫``_config.yml``,打开它,拉到最底下,做如下修改:
	  
	      ```yml
	      deploy:
	          type: 'git'   #这里应为git,如使用github会发生错误
	          repository: https://github.com/zqzess/zqzess.github.io    #把zqzess改成自己的用户名
	          branch: master
	      ```
	  
	      然后git bash执行``npm install hexo-deployer-git --save``安装部署插件
	      ![](https://cdn.jsdelivr.net/gh/zqzess/pichouse/pic/mintty_40ozYzOhzN.png)
	  
	      最后执行以下命令就可以部署上传了
	  
	      ``hexo g -d``
	  
	      g是generate缩写,d是deploy缩写
	  
	      然后就可以访问https://你的用户名.github.io查看博客了
- ## 写博客
  1. 新建文章
  
  git bash执行:``hexo new '文章标题'``
  
  完成后在`/source/_posts`下可以看到'文章标题.md'的文件，md是MarkDown的拓展名,网上可以找到它的语法
  
  文章写好依次后执行:
  
  ```
  hexo g
  ```
  
  ```
  hexo s
  ```
  
  然后可以在http://localhost::4000预览效果
  
  最后，发布到github，依次执行:
  
  ```
  hexo clean
  ```
  
  ```
  hexo g -d
  ```
  
  hexo clean可以请出缓存和已生成静态文件
  
  2. 草稿
  
  git bash执行:``hexo new draft '文章标题'``
  
  完成后在`/source/_drafts`下可以看到草稿
  
  发布草稿执行:``hexo publish [layout] <filename>``
### 写在最后
主题文件可以放在myBlog/themes/下面
后面我会写一篇关于主题美化及容易踩的坑和解决方案
#### 参考资料
- [使用hexo搭建github.io博客(一)](https://www.cnblogs.com/liulangmao/p/4323064.html)
- [超详细Hexo+Github Page搭建技术博客教程【持续更新】](https://segmentfault.com/a/1190000017986794)
- [三分钟在GitHub上搭建个人博客](https://segmentfault.com/a/1190000017986794)
- [搭建自己的github.io博客](https://blog.csdn.net/qq_34106574/article/details/82704883)