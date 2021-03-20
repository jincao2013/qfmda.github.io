# qfmda
This is a static website of Quantum Functional Materials Design and Application Laboratory. 



### 文件结构

qfmda.com的全部文件的目录结构：

```Bash
jindeiMac:website.qfmda jincao% pwd
/Volumes/jindedata/jindedata.bitphyswebdev/website.qfmda
jindeiMac:website.qfmda jincao% tree -L 2
.
├── resouce # 原始资料的备份
│   ├── 1-documents # 各种原始资料的备份
│   ├── 2-en_version # 英文版本，以前姚老师提过要弄，后来搁置了
│   ├── afdesign # 一些网址上用到的平面设计
│   └── publication-list # 已发表的论文列表
└── src # 网址的源代码
    ├── archive # 以.tar.gz格式发布的源代码
    ├── backup # 以前的代码，网页改版过好几次。这个文件夹里的东西基本上没用了，但还是备份了一下
    └── qfmda # 当前网址的源代码
```



`src/qfmda` 的目录结构

```Bash
jindeiMac:qfmda jincao% pwd
/Volumes/jindedata/jindedata.bitphyswebdev/website.qfmda/src/qfmda
jindeiMac:qfmda jincao% tree -L 1 -a
.
├── .git
├── .gitignore # 指定哪些文件不属于git
├── .idea # webstorm 的配置文件，已在gitignore里面屏蔽
├── README.md
├── bg.svg 
├── dist # css, js, fonts
├── en_dev # 英文版网址，还没有弄
├── files # 如果网页上有可以下载的东西，放这里
├── images # 图片都放这里
├── index.html # 网址的入口，默认是inde.html
├── index_en_dev.html # 英文网址的主页
├── index_zh.html # 中文网址的主页
├── logo.ico 
├── scripts # 更新网址用的脚本
├── yaogroup.svg 
└── zh # 中文网址的各个子页面

8 directories, 9 files
```



`src/qfmda/zh` 的目录结构

```bash
jindeiMac:zh jincao% tree -L 2
.
├── contact_us.html # 联系我们
├── group_activity.html 
├── highlight # 科研进展
│   ├── 20141006.html
│   ├── 20141106.html
│   ├── 20141202.html
│   ├── 20150504.html
│   ├── 20150820.html
│   ├── 20151019.html
│   ├── 20160512.html
│   ├── 20160531.html
│   ├── 20160919_1.html
│   ├── 20160919_2.html
│   ├── 20170227.html
│   ├── 20170420.html
│   ├── 20170510.html
│   ├── 20170907_1.html
│   ├── 20170907_2.html
│   ├── 20171202.html
│   ├── 20180123_1.html
│   ├── 20180123_2.html
│   └── 20180329.html
├── highlight.html # 科研进展
├── instrument.html 
├── join_us.html # 招生招聘
├── news
├── news.html# 最新动态
├── people.backup.2020.9.html
├── people.html # 团队成员
├── publications.html # 发表论文
└── research.html # 研究方向

2 directories, 29 files
```



### 如何修改网页内容

qfmda.com是静态网页(static website)，也就是说所有的页面都是事先编辑好的html格式的文档(超文本标记语言，可以理解成word，只不过是便于计算机在网上传播的格式)，通过url链接，访问每一个html。因此，修改网页内容，只需要修改对应的html。html规定的格式，可以参考`https://www.w3school.com.cn/html/index.asp`。



修改html推荐两种方式，小改，直接编辑就行，这里推荐 `notpad++` 或者 `sublime text`。大改，可以用专业一点的软件，这里只推荐`WebStorm`。



### 如何部署网址

以前我们采用的方案是，租一个服务器，服务器有公网ip地址，比如 `162.158.178.104`，在上面运行http服务，比如 `nginx` 或者 `Apache2`。这样通过这个ip地址就能访问我们的主页了。但是一般还需要一个好记的域名，把这个ip绑定到域名上.我们网站的域名是 `qfmda.com`，在DNS记录里添加 `A记录` 就行了。



最近发现 `coding` 这个平台，是基于Git的代码托管平台，可以自动部署(使用git push更新代码后，自动部署)。这个平台提供的有一个域名：`xxxxxx.coding-pages.com`。在DNS记录里添加`CNAME记录` ，可以重定向到其他域名。



以后准备使用后面的这个方案。



qfmda.com是已经购买的域名，moe的那个网址，域名还没有定，现在用的是腾讯云提供的域名`xxxxxx.coding-pages.com`。



### 常用git命令

``` Bash
git clone https://e.coding.net/quantumlab/qfmda/qfmda.git # 克隆远程库到本地

git add * # 添加文件到暂存区。
git commit -m "" # 将暂存区内容添加到仓库中。
git push origin master # 把当前master分支推送到远程服务器origin

git fetch origin master:master # 把远程仓库origin的master分支拉回到本地的master分支，如果是Fast-forward就执行合并，如果有冲突则不合并
git merge FETCH_HEAD # 合并origin/master到工作区

git remote set-url origin https://e.coding.net/quantumlab/qfmda/qfmda.git # 关联本地代码库和远程代码库

git status # 查看仓库当前的状态，显示有变更的文件。
git log # 查看历史提交记录

git archive --format tar.gz --output "../archive/qfmda.year.mouth.tar.gz" master # 打包当前版本到 "../archive/qfmda.year.mouth.tar.gz"

git config -l # 查看当前git的配置
```



参考：

git: https://www.runoob.com/git/git-tutorial.html

Html: https://www.w3school.com.cn/html/index.asp