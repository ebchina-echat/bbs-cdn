# bbs-cdn
全球免费CDN库

## 发版步骤及相关注意点

> 还没有 git 工具：见 **[下文](#生成对应ssh密钥)**

一、在项目（不是本仓库）根目录下，运行相应的命令
> 使用命令：npm version <update_type> 进行修改，update_type 有三个参数:
> -  patch：这个是补丁的意思，补丁最合适；
> -  minor：这个是小修小改；
> -  major：这个是大改咯；

简单点说，假如当前版本为：1.0.0
- 比如我想来个 1.0.1 版本，注意，是最后一位修改了增 1，那么命令：`$ npm version patch`
- 比如我想来个 1.1.0 版本，注意，是第二位修改了增 1，那么命令：    `$ npm version minor`
- 比如我想来个 2.0.0 版本，注意，是第一位修改了增 1，那么命令：    `npm version major`

**注意 $ 只是用来表示是在命令行环境中（下同），可千万别复制哈** 

这里以小版本为例： 

`$ npm version patch`  

二、在项目根目录下，运行打包命令

`$ npm run build`

三、清空本仓库 dist 所有目录，将打包生成的 dist 目录直接复制过来就可以

`$ git add .`

`$ git commit -m "Update Version version(修改成对应的版本号)"`

> 此处可能需登录账号，如果拉代码用 ` git clone git@github.com:ebchina-echat/bbs-cdn.git ` 可以免去，前提是先配置 ssh 密钥，详见 **[下文](#生成对应ssh密钥)**

`$ git push -u origin master `

## 检查是否生效
从 dist 目录中随便复制一个静态文件链接，检查一下，比如：
https://cdn.jsdelivr.net/gh/ebchina-echat/bbs-cdn@1.2.0/dist/js/app.7950609e.js

## 获取历史包
将下方的链接中 ${version} 换成相对应的版本号即可回退版本，记住对应的 index.html 也得同步更改
- https://cdn.jsdelivr.net/gh/ebchina-echat/bbs-cdn@${version}/dist/js/app.7950609e.js

## todo

- 推到 dev 分支即可，剩下的交给 CI 去解决

## 生成对应 ssh 密钥，免去登录

### 安装 Git

如果你先前已使用过 [Git](https://gitforwindows.org/) 来作为你进行项目开发时的默认命令行工具，则该工具将会默认为你安装好 Git。

使用以下命令来检测是否成功安装：
最好使用刚刚下载好的 <kbd>git</kbd> 或者, 按<kbd>Alt</kbd>+<kbd>R</kbd> 在弹出框中输入<kbd>cmd</kbd>，<kbd>Enter</kbd>回车，再在命令行中输入，`git --version` ， 如下：
```
$ git --version
git version 2.26.2.windows.2
```
生成 SSH Key，请将  <kbd>your_email@example.com</kbd> 替换为你的邮箱：

```
$ ssh-keygen -t rsa -C "your_email@example.com"
Generating public/private rsa key pair.
```
剩下的可以都选择默认，一路 <kbd>Enter</kbd> 键即可，完成以后，输入：`cat ~/.ssh/id_rsa.pub`，将生成的密钥上传到 github 中。

申请个github账号，登陆后，点击 [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new),将公钥粘贴上去，就欧克了！
