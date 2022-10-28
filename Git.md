# Git

## 0.Git 下载安装与配置

**Git 是啥?**：https://juejin.cn/post/6994244897138016270

**下载安装**：https://blog.csdn.net/huangqqdy/article/details/83032408>

**环境配置**：https://www.cnblogs.com/ldq678/p/13287924.html?utm_source=tuicool

## 1.Git 学习

**git 命令练习沙盒**：https://learngitbranching.js.org/?demo=&locale=zh_CN

**git 基本命令行用法讲解**：https://www.bilibili.com/video/BV1WW411Q7EW

## 2.部分常用指令

```git
git clone https://github.com/xxx   （克隆项目）
git branch                 （查看当前分支）
git branch  分支名          （创建分支）
git checkout 分支名         （切换分支）
git add .                  （注：别忘记后面的.，此操作是把Test文件夹下面的文件都添加进来）
git commit  -m  "注释"      （注：“提交信息”里面换成你需要，如“first commit”）
git push -u origin master  （注：此操作目的是把本地仓库push到github上面，此步骤需要你输入帐号和密码）
```

### 2.0 `git help ` 帮助信息

- 使用命令`git help`获取常用的 git 操作信息
- 使用命令`git help -a`显示所有命令
- 使用命令`git help -g`查看 git 使用手册
- 使用命令`git help 具体功能` 查看该功能下的所有可用选项

### 2.0 `git config ` 配置 git

- 使用命令`git config --global user.name="张三"`修改配置
- 使用命令`git config --list`查看配置
- 使用命令`git config --unset --global user.email`清除指定配置
- 使用命令`git config --global color.ui true` 设置 ui

### 2.0 `git status `

- 使用命令`git status` 查看对哪些文件作了修改
  ![image-20221028204322089](http://smilehanup.top/typora_20221025/image-20221028204322089.png)

### 2.0 `git init` 初始化项目

在文件夹下使用命令 `git init`（当前目录） 或 `git init filename`（创建文件夹） 初始化项目，在目标文件夹下创建`.git`文件。之后便可记录在该目录下所做的所有更改。

```bash
$ git init
$ 或
$ git init filename
```

### 2.0 `git add .` 添加需要 commit 的文件

首先需要 add 修改的文件，然后才能执行 commit 操作

```bash
$ git add .               // 添加所有文件
$ 或
$ git add index.html      // 添加指定文件
```

### 2.0 `git commit -m "**"` 提交记录

- 使用命令`git commit -m "**"`将修改内容提交到本地暂存区，注意：① `-m`和注释内容是必须的；② 提交前需要先执行命令`git add`
- 也可以使用命令`git commit -am "**"`，在 commit 前执行 add 操作
- 如果没有加`-m` ，解决办法见[章节 3.1](##31-git commit 没加 -m)

```bash
$ git commit -m "这里面写注释"
$ 或
$ git commit -am "不用先git add . 直接提交"
```

- `git commit`过程示意图

<img src="http://smilehanup.top/typora/image-20221019155518150.png" alt="image-20221019155518150"  />

### 2.0 `git diff` 对比发生的修改

使用命令`git diff`查看做了哪些修改。

```bash
$ git diff               // 查看所有修改
$ 或
$ git diff index.html   // 查看单个文件的修改
```

<img src="http://smilehanup.top/typora_20221025/image-20221027221043712.png" alt="image-20221027221043712" style="zoom: 50%;" />

### 2.0 `git rename` 重命名文件

先手动把 theme.css 重命名为 style.css（注意先做这一步，不然 git 会直接把 theme.css 文件删除），再使用命令 `git rm theme.css`和`git add style.css`告诉 git 把 theme.css 文件重命名为 style.css

```bash
$ 第一步先重命名文件
$ git rm theme.css     // 第二步：告诉git移除了文件theme.css
$ git add style.css    // 第三步：告诉git新增了文件style.css
$ 完成上述步骤之后，git即记录为theme.css更名成了style.css
```

![image-20221027215835559](http://smilehanup.top/typora_20221025/image-20221027215835559.png)

### 2.0 `git mv` 移动文件/修改文件名

**git mv 修改文件名**

使用命令`git mv oldname.css newname.css`把旧文件名修改为新文件名

```bash
git mv oldname newname      //把旧文件名修改为新文件名
```

<img src="http://smilehanup.top/typora_20221025/image-20221027221607330.png" alt="image-20221027221607330"  />

**git mv 移动文件**

使用命令`git mv style.css path/`把 style.css 文件移动到路径 path 下

```bash
$ git mv filename pathname/      // 移动文件到指定目录下
```

![image-20221027222122713](http://smilehanup.top/typora_20221025/image-20221027222122713.png)

### 2.0 `git rm` 删除文件/文件夹

使用命令`git rm path/style.css`或`git rm a.html b.html c.html`删除单个或多个文件

```bash
$ git rm path/style.css
$ 或
$ git rm a.html b.html c.html
```

![image-20221027223334832](http://smilehanup.top/typora_20221025/image-20221027223334832.png)

### 2.0 `git HEAD` 恢复文件

- 使用命令`git checkout HEAD -- index.html`恢复文件到上一次提交的状态，
- 使用命令`git checkout HEAD^ -- index.html`恢复文件到上上次提交的状态
- 区别在于`^`符号的个数，文件被删除或修改都能恢复

```bash
$ git checkout HEAD -- index.html     // 恢复文件到上一次提交的状态
$ git checkout HEAD^ -- index.html    // 恢复文件到上上次提交的状态
$ git checkout HEAD^^ -- index.html   // 恢复文件到上上上次提交的状态
……
```

![image-20221027224422827](http://smilehanup.top/typora_20221025/image-20221027224422827.png)

### 2.0 `git revert `

### 2.0 `git reset `

### 2.0 `git branch ` 分支操作

- 使用命令`git branch mybranch `**创建一个新的分支**
- 使用命令`git branch`或`git branch --list`**查看所有分支**。
- 创建分支后，使用命令`git checkout smilebug`**切换到分支**，此时对项目做的更改只会影响到 smilebug 分支，而不会影响到 master 分支
- 使用命令`git branch -m bagfix bugFix`**重命名分支**
- 使用命令`git branch -d bugFix`**删除分支**
- 如果已经与远程 github 仓库建立连接，可以使用命令`git branch -a`**查看所有本地分支**，使用命令`git branch -r`**查看所有远程分支**

```bash
$ git branch smilebug           // 创建新分支
$ git checkout smilebug         // 切换到分支
$ git branch                    // 查看所有分支
$ 或
$ git branch --list             // 查看所有分支
$ git branch -m bagfix bugFix   // 重命名分支
$ git branch -d bugFix          // 删除分支
$ git branch -a                 // 查看所有本地分支
$ git branch -r                 // 查看所有远程分支
```

![image-20221028145652833](http://smilehanup.top/typora_20221025/image-20221028145652833.png)

- 查看本地分支和远程分支。注意不能切换到 origin/master 分支，因为是用于远程仓库进行版本控制的。

  ![image-20221028200831435](http://smilehanup.top/typora_20221025/image-20221028200831435.png)

- 创建分支的过程示意图

![image-20221019160302466](http://smilehanup.top/typora/image-20221019160302466.png)

### 2.0 `git checkout ` 切换分支

使用命令`git checkout master`切换到 master 分支，使用`git checkout -b smilebug `创建并切换到 smilebug 分支

```bash
$ git checkout master   // 切换到指定分支
```

### 2.0 `git diff branch1..branch2` 对比分支之间的区别

- 使用命令`git diff master..smilebug`对比两个分支所有文件之间的差异
- 或使用命令`git diff master..smilebug index.html`对比两个分支中 index.html 文件内容的差别
- a 是左边的分支，b 是右边的分支。**+-是右边分支的文件内容相对于左边分支的文件内容来看的**。

```bash
$ git diff master..smilebug              // 对比两个分支所有文件内容的差别
$ 或
$ git diff master..smilebug index.html   // 对比两个分支指定文件内容的差别
```

<img src="http://smilehanup.top/typora_20221025/image-20221028151427539.png" alt="image-20221028151427539" style="zoom: 67%;" />

### 2.0 `git merge` 合并分支

比如当前在 master 分支上，使用命令`git merge smilebug`后，就**把 smilebug 分支上做的修改合并到 master 上**了。

**fast forward**

- 当在创建 smilebug 分支以后，还没有对 master 作新的提交时，此时在 master 分支上使用命令`git merge smilebug`执行的合并就是`fast forward`的合并，也就是会直接把 smilebug 分支上的修改合并到 master 分支上去。
- 这个合并不会是一个新的提交。
- 注意：因为这里 smilebug 是从 master 中新建的分支，所以刚开始两者的内容是一模一样的。又因为在 smilebug 分支上做了更改后，由于 master 没有再执行 commit 即没有发生更改，所以相当于 smilebug 中做的更改就是发生的所有更改。

**git merge 真正的合并**

- 当在 master 分支上创建 smilebug 分支，并且对 master 分支做了新的提交之后。此时的 master 已经和创建 smilebug 分支时的 master 不一样了，此时的合并才是更常见的合并。这种合并有时候会遇到**冲突**，所以合并前需要先解决冲突。

**git conflict 冲突解决**

- 下图中的冲突解决方法有：1、点击执行操作中的命令进行保留；2、直接删除不需要的代码，包括<<==>>等内容
- 然后执行命令`git add .`和命令`git commit`。不加`-m`也会自动创建注释，使用`:wq`保存并退出

![image-20221028160506115](http://smilehanup.top/typora_20221025/image-20221028160506115.png)

- 合并分支的过程示意图（把 bugFix 分支合并到 main 上）

![image-20221019162230932](http://smilehanup.top/typora/image-20221019162230932.png)

### 2.0 `git rebase` 合并分支

第二种合并分支的方法是 `git rebase`。Rebase 实际上就是取出一系列的提交记录，“复制”它们，然后在另外一个地方逐个的放下去。Rebase 的优势就是可以创造更线性的提交历史，这听上去有些难以理解。如果只允许使用 Rebase 的话，代码库的提交历史将会变得异常清晰。

```bash
git checkout -b bugFix   // 创建并切换到分支bugFix
git commit               // 提交
git checkout main        // 切换分支
git commit               // 提交
git checkout bugFix      // 切换分支
git rebase main          // 合并到main分支
```

![image-20221019170446045](http://smilehanup.top/typora/image-20221019170446045.png)

### 2.0 `git stash `

保存工作进度

### 2.0 `git log ` 查看日志

```bash
$ git log                                          // 查看所有日志的详细信息
$ 或
$ git log --oneline                                // 查看所有日志，且每行显示一条
$ 或
$ git log --oneline -5                             // 仅显示5行
$ 或
$ git log --oneline --author="smile"               // 包含指定作者的提交
$ 或
$ git log --oneline --grep="index.html"            // 包含指定内容的提交
$ 或
$ git log --oneline --before="2020-10-10"          // 指定时间段内的提交
$ git log --oneline --before="1 week"
$ git log --oneline --before="3 days"
$ 或
$ git log --oneline --graph                        // 包含分支图形的日志
$ 或
$ git log --oneline --decorate --all -10 --graph   // 查看日志、显示10条、分支图形展示
$ 或
$ git help log                                     // 查看所有log命令的使用手册
```

### 2.0 `alias ` 设置别名

使用命令`git config --global alias.co checkout`为`git checkout`设置别名`git co`。设置其余命令同理。

```bash
$ git config --global alias.co checkout  // 为checkout命令设置别名
$
$ git co master                          // 使用别名执行命令
```

### 2.0 `ignore ` 添加全局忽略跟踪修改文件

有时候不想让项目中的某些文件被跟踪

![image-20221028191529475](http://smilehanup.top/typora_20221025/image-20221028191529475.png)

### 2.0 `.gitignore ` 为每个项目设置忽略跟踪修改文件

为每个项目单独设置忽略跟踪的文件，可以在项目的根目录创建 .gitignore 文件，然后在里面添加需要忽略的文件，比如"access.log"。

![image-20221028192424656](http://smilehanup.top/typora_20221025/image-20221028192424656.png)

### 2.0 `remote ` 远程版本库

为项目在远程服务器上创建版本库，然后把本地的版本库推送到服务器上。

### 2.0 `origin ` 创建 git 仓库

- 创建 git 仓库（需要在本地初始化 git）

<img src="http://smilehanup.top/typora_20221025/image-20221028193653925.png" alt="image-20221028193653925" style="zoom: 80%;" />

![image-20221028195445545](http://smilehanup.top/typora_20221025/image-20221028195445545.png)

- 把本地创建的 git 项目推送上去：`git remote add origin https://github.com/smilehan2333/demo_gitcommand.git`
- 查看远程的名称：`git remote` // origin
- 查看远程操作：`git remote -v` // 有 fetch 和 push 操作

![image-20221028195412604](http://smilehanup.top/typora_20221025/image-20221028195412604.png)

### 2.0 `git push ` 远程推送

- 在本地创建好 git 仓库后，使用命令`git push -u 远程名称 分支名称`将本地 git 项目推送至远程。

![image-20221028195733735](http://smilehanup.top/typora_20221025/image-20221028195733735.png)

- 此时 github 中就已经有了本地推送的 master 分支上的项目

![image-20221028200029183](http://smilehanup.top/typora_20221025/image-20221028200029183.png)

- 同理可以再次使用命令`git push -u origin smilebug`将其余分支推送到远程仓库

### 2.0 `git remote workflow `

### 2.0 `git clone ` 克隆项目

其余用户也可以使用命令`git clone https://github.com/smilehan2333/demo_gitcommand.git`从远程克隆代码。

```bash
$ git clone https://github.com/smilehan2333/demo_gitcommand.git
```

### 2.0 `git fetch ` 从远程版本库获取更新

- 当仓库所有者对远程版本库做了更改后，其余用户不能及时获取更新，就可以使用`git fetch`从远程仓库获取最新的代码
- 然后就可以使用命令`git merge origin/master` 合并一下更新。

### 2.0 `fork `

### 2.0 `pull request `

### 2.0 `git collaborator `

贡献

### 2.0 `github tools `

github 图形化工具

### 2.0 `brackets git `

## 3.常见报错

### 3.1 git commit 没加 -m

- Please enter the commit message for your changes. Lines starting # with '#' will be ignored
- 原因是提交的命令为：`git commit`
- 修改提交命令为：`git commit -m "注释"`
- 如何退出：`:wq`
- 解决方法详见：[【Git 基础篇】git commit 没有加-m，进入到 vim 编辑器后该如何操作？](https://www.jianshu.com/p/5ceb52619ffd)

### 3.2 [Git 报错解决：OpenSSL SSL_read: Connection was reset, errno 10054 错误解决](https://blog.csdn.net/weixin_43945983/article/details/110882074)

首先，造成这个错误很有可能是网络不稳定，连接超时导致的，如果再次尝试后依然报错，可以执行下面的命令。

**打开 Git 命令页面，执行 git 命令脚本：修改设置，解除 ssl 验证**

`git config --global http.sslVerify "false"`

###

# github 开源项目

- 免费简历生成器：Reactive Resume https://github.com/AmruthPillai/Reactive-Resume

  - [本地构建](https://docs.rxresu.me/source-code/local-build)：

    - 安装 pnpm：`npm i -g pnpm`;[什么是 pnpm](https://blog.csdn.net/Dylan666d/article/details/114002666)
    - 安装依赖：`pnpm install`

    - 将`.env.example`文件复制到`.env`项目根目录中
    - 使用以下命令在本地运行应用程序：`pnpm dev`
    - 通过运行以下命令在部署之前构建项目：`pnpm build`
    - 最后，通过运行以下命令启动所有三个工作区的生产服务器：`pnpm start`

- CSS 样式：B 站 upLibra11 项目地址：https://github.com/Libra11/CSS-EFFECT
