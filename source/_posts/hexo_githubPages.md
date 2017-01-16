---
title: Hexo+GithubPages搭建个人博客
tags: [Hexo]
---
[nodejs_id]: https://nodejs.org/
[git_id]: https://git-scm.com/
[homebrew_id]: http://brew.sh/
[macports_id]: https://www.macports.org/
[gitinstall_id]: https://sourceforge.net/projects/git-osx-installer/
[windows_git_id]: https://git-scm.com/download/win
[nvm_id]: https://github.com/creationix/nvm
[localhost_id]: http://localhost:4000/
[github_pages_id]: https://pages.github.com/
[div_io_id]: http://div.io/topic/1691
[jianshu_id]: http://www.jianshu.com/p/05289a4bc8b2
[gitbook_id]: https://pengloo53.gitbooks.io/hexo/content/

## 什么是Hexo？
**Hexo** 是一个快速、简单且强大的框架。Hexo使用**Markdown**（或其他渲染引擎）解析您的文章。并在几秒钟内，透过漂亮的主题产生**静态**档案。
## 安装Hexo
安装**Hexo**必须先检查电脑是否已经安装下列软件:
* [Node.js][nodejs_id]</br>
* [Git][git_id]

以上必备软件安装好后我们就可以通过npm完成hexo的安装。

## 这里说下我电脑的系统环境
~~~
➜  ~ hexo -v
hexo-cli: 1.0.2
os: Darwin 16.3.0 darwin x64
http_parser: 2.7.0
node: 4.5.0
v8: 4.5.103.37
uv: 1.9.1
zlib: 1.2.8
ares: 1.10.1-DEV
icu: 56.1
modules: 46
openssl: 1.0.2h
---------- 只供参考 --------
--如安装遇到问题请自行Google--
~~~

#### 安装Git
* Windows：下載並安裝 [git][windows_git_id]。
* Mac：使用 [Homebrew][homebrew_id], [MacPorts][macports_id] 或 [安裝程式][gitinstall_id] 安裝。
* Linux (Ubuntu, Debian)：sudo apt-get install git-core。
* Linux (Fedora, Red Hat, CentOS)：sudo yum install git-core。

#### 安装Node.js
安装Node.js的最佳方式是通过[nvm][nvm_id]，当然还有很多安装方式但是我还是建议使用nvm。</br>
cURL:
~~~
$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh
~~~
Wget:
~~~
$ wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh
~~~
安裝完成，重启终端并执行下列指令以安裝 Node.js。
~~~
$ nvm install stable
~~~
#### 安装Hexo
一旦Git和Node.js安装好后就可以通过**npm**安装Hexo。
~~~
 cd Desktop/
 npm install -g hexo-cli
 hexo init blog
 cd blog
 npm install // 安装各种库
 hexo g // 或者hexo generate
 hexo s // 或者hexo server, 然后在http://localhost:4000/ 查看
~~~

## Hexo指令
#### 常用命令
~~~
 hexo generate //(hexo g)生成静态文件，会在当前目录下生成一个新的叫做public的文件夹
 hexo server //(hexo s)启动本地web服务，用于博客的预览
 hexo deploy //(hexo d)部署播客到远端（比如github, heroku等平台）
 hexo new "postName" //新建文章
 hexo new page "pageName" //新建页面
~~~
#### 常用简写
~~~
 hexo n == hexo new
 hexo g == hexo generate
 hexo s == hexo server
 hexo d == hexo deploy
~~~

## Hexo主题设置
这里以主题landscape为例进行说明。
#### 设置主题
修改Hexo目录下的_config.yml配置文件中的theme属性，将其设置为landscape。
#### 更新主题
~~~
cd themes/yilia
git pull
hexo g // 生成
hexo s // 启动本地web服务器
~~~
现在打开 [http://localhost:4000/][localhost_id] ，会看到我们已经应用了一个新的主题。</br>
------**以上部分都是在本地接下来我们配置githubPages把博客搭载到git服务上**-----
## GithubPages配置
#### 什么是GithubPages？
[GithubPages][github_pages_id]用于介绍托管在GitHub的项目，不过，由于他的空间免费稳定，用来做搭建一个博客再好不过了,还有七牛也是免费的看你自己的选择。</br>
每个帐号只能有一个仓库来存放个人主页，而且仓库的名字必须是username/username.github.io，这是特殊的命名约定。你可以通过http://username.github.io 来访问你的个人主页。</br>
这里特别提醒一下，需要注意的个人主页的网站内容是在master分支下的。
#### 创建自己的Github Pages
##### github上建立仓库
登录后系统，在github首页，点击页面右下角「New Repository」
填写项目信息：

project name：xxxxx.github.io

description： Writing 1000 Words a Day Changed My Life
注：Github Pages的Repository名字是特定的，比如我Github账号是xxxxx，那么我Github Pages Repository名字就是xxxxx.github.io。
点击「Create Repository」 完成创建。
## 将独立域名与GitHub Pages的空间绑定
方法一：在Repository的根目录下面，新建一个名为CNAME的文本文件，里面写入你要绑定的域名，比如cnfeat.com。

方法二：到我的github仓库，点击右下角的「Download ZIP」，下载源文件，解压，找到CNAME文件，用记事本打开，将cnfeat.com修改成你的域名，放进Hexo\source目录下，用hexo命令提交上去。

~~~
hexo d -g // 把修改的文件上传的git
~~~
## 参考链接
#### [Hexo][div_io_id]
#### [如何搭建一个独立博客][jianshu_id]
#### [Hexo小书][gitbook_id]


