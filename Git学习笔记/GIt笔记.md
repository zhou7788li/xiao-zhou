

# GIt笔记

## 一、两种本本控制器

### 1、集中式版本控制器

![img](GIt笔记.assets/QQ_1721182163066.png)

#### 操作：

从中央服务器下载最新版本

修改完成后在上传到中央服务器

#### 优点：

操作简单

#### 缺点：

中央服务器出现问题，所有人工作将无法进行，只能等待服务器恢复运行

### 2、分布式版本控制系统

![img](GIt笔记.assets/QQ_1721182562917.png)

#### 操作：

从中央服务器拉取数据，对数据进行修改，添加到暂存区，提交到本地数据库，推送到中央服务器

#### 优点：

免费开源，速度快，功能强大，支持离线工作以及强大的分支管理的特性

可以在本地进行修改，不需要考虑网络问题

即使中央服务器出现问题，也可以进行工作

#### 缺点：

中央服务器出现问题，所有人工作将无法进行，只能等待服务器恢复运行

## 二、Git安装与配置

### 1、下载安装

#### Git官方网站：

https://git-scm.com/

#### 下载并安装完成：

![img](GIt笔记.assets/QQ_1721183274560.png)

#### 查看Git是否安装成功：

在终端中输入：git -v

![img](GIt笔记.assets/QQ_1721183478222.png)

即安装成功

#### 打开 GIt Bash Here

在资源管理器中右键

![img](GIt笔记.assets/QQ_1721183683646.png)

点击 GIt Bash Here 打开

### 2、配置用户名邮箱

#### 用户名：

如果用户名中有空格需要用双引号，没有则不需要

命令：git config --global user.name "用户名“

#### 邮箱：

命令：git config --global user.email 邮箱

![img](GIt笔记.assets/QQ_1721184190156.png)

#### 保存密码：

命令：git config --global credential.helper store

#### 查看配置信息：

命令：git config --global --list

![img](GIt笔记.assets/QQ_1721184623987.png)

## 三、创建仓库

### 1、创建本地仓库

首先，找到一个合适位置创建空目录，在资源管理器合适位置，右键，点击 GIt Bash Here 打开

#### 创建目录

命令：mkdir  目录名

进入目录：cd 目录名

#### 创建本地仓库

命令：git init

![img](GIt笔记.assets/QQ_1721185477339.png)

初始化一个空的Git仓库是一个非常基础且重要的步骤。这个过程通常使用`git init`命令来完成。该命令会创建一个新的隐藏目录`.git`，其中包含了一些用于跟踪代码变更的元数据和配置文件

#### 查看本地仓库是否有 .git目录

命令：ls -a

![img](GIt笔记.assets/QQ_1721201220648.png)

查看有.git目录，则创建成功

.git目录如果被删除，则该目录不在是本地仓库

![img](GIt笔记.assets/QQ_1721201356371.png)

### 2.克隆远程仓库

命令：git clone 仓库链接

![img](GIt笔记.assets/QQ_1721201607107.png)

##  四、git的工作区域和文件状态

###   1、git的本地管理区域



![img](GIt笔记.assets/QQ_1721202103649.png)

![img](GIt笔记.assets/QQ_1721202197007.png)



## 五、添加文件和提交文件

### 1、查看仓库文件状态

```
git status
```

创建一个文本文件：

```git
echo  ”这是第一个文件“ > file1.txt
```

![img](GIt笔记.assets/QQ_1721202618554.png)

![img](GIt笔记.assets/QQ_1721202651601.png)

红色为 未跟踪

#### 添加文件到暂存区

```
git add 文件名
```

```
git add . //将所有文件添加到暂存区
```

```
git add *.txt  //使用通配符，将后缀为.txt的文件添加到暂存区
```

![img](GIt笔记.assets/QQ_1721203506888.png)

![img](GIt笔记.assets/QQ_1721202796424.png)

文件已经添加到暂存区会变为绿色

#### 查看暂存区内容

```
git ls-files
```

![img](GIt笔记.assets/QQ_1721202918899.png)

### 2、将文件提交到本地仓库中

#### 文件提交

只有在暂存区中的文件会被提交

```
git commit -m "提交说明"
```

#### 查看提交记录

```
git log
```

![img](GIt笔记.assets/QQ_1721203891358.png)

#### 查看简洁的提交信息

```
git log --oneLine
```

![img](GIt笔记.assets/QQ_1721203974752.png)

## 六、git reset 回退版本，三种模式

### 1、三种模式

![img](GIt笔记.assets/QQ_1721204141886.png)

打勾：表示保留

打叉：清空



![img](GIt笔记.assets/QQ_1721204355480.png)



### 2、回退版本

#### git reset --soft

```
git reset --soft 回退版本id
```

![img](GIt笔记.assets/QQ_1721204830903.png)

![img](GIt笔记.assets/QQ_1721204845860.png)

![img](GIt笔记.assets/QQ_1721205013171.png)

#### git reset --hard

```
git reset --hard  回退版本id/HEAD^为回退上一个版本
```

![img](GIt笔记.assets/QQ_1721205329898.png)

![img](GIt笔记.assets/QQ_1721205340782.png)

![img](GIt笔记.assets/QQ_1721205399290.png)

#### git reset  

```
git reset --HEAD^  //回退到上一个版本
```

![img](GIt笔记.assets/QQ_1721205557399.png)

![img](GIt笔记.assets/QQ_1721205568030.png)

![img](GIt笔记.assets/QQ_1721205627413.png)

如果觉得之前提交的多个版本，但是又觉得这些提交没有太多意义，可以合并成一个版本的时候可以通过

git reset --soft 可以直接提交

git reset  退回之后重新添加到暂存区，然后提交

git reset --hard 谨慎操作

如果误操作可以查看操作历史

#### 查看操作历史

```
git reflog
```

![img](GIt笔记.assets/QQ_1721207092054.png)

##  七、使用git diff 查看版本差异

## 

![img](GIt笔记.assets/QQ_1721379678247.png)

### 1、工作区   与  暂存区    的差异：git  diff

默认查看工作区与暂存区的差异

显示差异的详细信息

![img](GIt笔记.assets/QQ_1721379701514.png)

##### 案例

版本记录

![img](GIt笔记.assets/QQ_1721380191396.png)

原提交文件内容

![img](GIt笔记.assets/QQ_1721380237718.png)

更改本地文件的内容

删除：333、添加 ：一键三联了吗？

![img](GIt笔记.assets/QQ_1721380390716.png)

使用 git diff  查看差异

![img](GIt笔记.assets/741b1a2d242f02665d0385e3918b3702.png)

把全部文件添加到暂存区

![img](GIt笔记.assets/QQ_1721381002498.png)

查看工作区与暂存区的差异显示无内容

![img](GIt笔记.assets/QQ_1721381150568.png)

### 2、工作区   与   版本区    的差异：git diff HEAD

![img](GIt笔记.assets/QQ_1721394577238.png)

![img](GIt笔记.assets/QQ_1721394595400.png)

### 3、暂存区   与   版本区的差异：git diff   --cached

![img](GIt笔记.assets/QQ_1721394419609.png)

![img](GIt笔记.assets/QQ_1721394633705.png)

### 4、   版本    与   版本    之间的差异：git diff 提交id   提交id

先查看提交历史版本

![img](GIt笔记.assets/QQ_1721394875976.png)

##### 查看版本与上一个版本之间的差异：git diff 提交id   HRAD

##### ![img](GIt笔记.assets/QQ_1721395029220.png)

##### 版本与上一个版本之间的差异：git diff HEAD~  HRAD

HRAD：表示第二个版本

HEAD~  或HEAD^：表示当前最新版本

HEAD~数字：表示最新版本之后的第几个版本

##### 加上文件名后只会查看该文件的差异 

```
git diff HEAD~  HRAD   文件名
```

![img](GIt笔记.assets/QQ_1721395594942.png)

##### 总结

![img](GIt笔记.assets/QQ_1721396582500.png)

## 八、git rm 删除文件

### 1、删除本地文件： rm  文件名

![img](GIt笔记.assets/QQ_1721703091542.png)

查看仓库状态

![img](GIt笔记.assets/QQ_1721703158862.png)

查看暂存区内容

![img](GIt笔记.assets/QQ_1721703251865.png)

把本地文件添加到暂存区

![img](GIt笔记.assets/QQ_1721703288002.png)

### 2、删除暂存区内容：git rm  文件名

 删除暂存区文件；工作区文件也会被删除

![img](GIt笔记.assets/QQ_1721703461747.png)

查看版本库状态

![img](GIt笔记.assets/QQ_1721703497969.png)

查看工作区文件和暂存区

![img](GIt笔记.assets/QQ_1721703588342.png)

### 3、删除仓库文件：git rm --cached 文件名

![img](GIt笔记.assets/QQ_1721708718008.png)

#### 最后记得提交到版本库中

![img](GIt笔记.assets/QQ_1721703725603.png)

### 总结

![img](GIt笔记.assets/QQ_1721703736355.png)

## 九、.gitignore 忽略文件



### .gitignore 忽略文件的匹配规则

从上到下逐行匹配，每一行表示一个忽略模式

![img](GIt笔记.assets/QQ_1721725528674.png)

![img](GIt笔记.assets/QQ_1721725668798.png)

![img](GIt笔记.assets/QQ_1721725784134.png)



![img](GIt笔记.assets/QQ_1721706488450.png)

#### 1、创建一个日志文件

![img](GIt笔记.assets/QQ_1721706724769.png)

#### 2、在创建一个日志文件

![img](GIt笔记.assets/QQ_1721706833685.png)

![img](GIt笔记.assets/QQ_1721707147795.png)

#### 3、添加暂存区和提交版本

![img](GIt笔记.assets/QQ_1721707272401.png)

#### 4、查看仓库文件

![img](GIt笔记.assets/QQ_1721707320985.png)

编辑.gitignore 忽略文件

![img](GIt笔记.assets/QQ_1721707468509.png)

#### 5、在.gitignore 忽略文件使用聚合函数

![img](GIt笔记.assets/QQ_1721707496982.png)

![img](GIt笔记.assets/QQ_1721725218424.png)

![img](GIt笔记.assets/QQ_1721725288672.png)

#### 6、添加日志文件

<img src="GIt笔记.assets/QQ_1721707563238.png" alt="img" style="zoom: 200%;" />

#### 7、提交版本，查看本地仓库内容

![img](GIt笔记.assets/QQ_1721707714776.png)

#### 修改工作目录日志文件

![img](GIt笔记.assets/QQ_1721708437648.png)

#### git diff 查看工作区与暂存区的差异

![img](GIt笔记.assets/QQ_1721708531042.png)

如果文件已经被提交到仓库中，需要先删除仓库中的文件

#### 删除仓库文件

![img](GIt笔记.assets/QQ_1721708793066.png)

#### 提交版本

.log文件如何修改都不会被纳入版本控制中，就是忽略了.log文件

![img](GIt笔记.assets/QQ_1721709000861.png)

![img](GIt笔记.assets/QQ_1721709122336.png)







### 查看暂存区文件：git diff --cached

### 工作目录中的空文件夹不会被纳入管理

## 十、SSH配置和克隆仓库

### 1、GitHub创建仓库![img](GIt笔记.assets/QQ_1721726279485.png)

![img](GIt笔记.assets/QQ_1721726311794.png)

![img](GIt笔记.assets/QQ_1721726380035.png)

![img](GIt笔记.assets/QQ_1721726473404.png)

![img](GIt笔记.assets/60964642ab7e5f5cabe35cc236d25680.png)

### 2、配置SSH密钥

![img](GIt笔记.assets/d4593caccb740f4200b1739999c97837.png)

![img](GIt笔记.assets/QQ_1721727122901.png)

![img](GIt笔记.assets/QQ_1721727134728.png)

![img](GIt笔记.assets/QQ_1721727154420.png)

![img](GIt笔记.assets/QQ_1721727182138.png)

![img](GIt笔记.assets/QQ_1721727207304.png)

![img](GIt笔记.assets/QQ_1721727218676.png)

它会在我们用户根目录的点SSH日录下生成一个id_rsa的密钥文件

![img](GIt笔记.assets/QQ_1721727289751.png)

![img](GIt笔记.assets/QQ_1721727297809.png)

![img](GIt笔记.assets/QQ_1721727307593.png)

![img](GIt笔记.assets/QQ_1721727317301.png)

![img](GIt笔记.assets/QQ_1721727323489.png)

![img](GIt笔记.assets/f6f753e0d608a3cc60ba94477c1bfbce.png)

回车

![img](GIt笔记.assets/QQ_1721727418482.png)

![img](GIt笔记.assets/QQ_1721727433276.png)

![img](GIt笔记.assets/QQ_1721727448238.png)

![img](GIt笔记.assets/QQ_1721727459196.png)

![img](GIt笔记.assets/QQ_1721727485934.png)

进入  .pub文件

![img](GIt笔记.assets/QQ_1721727543024.png)

![img](GIt笔记.assets/QQ_1721727509695.png)

![img](GIt笔记.assets/QQ_1721727583196.png)

![img](GIt笔记.assets/QQ_1721727595917.png)

![img](GIt笔记.assets/QQ_1721727617101.png)

![img](GIt笔记.assets/QQ_1721727645112.png)

![img](GIt笔记.assets/QQ_1721727706786.png)

![img](GIt笔记.assets/QQ_1721727726253.png)

![img](GIt笔记.assets/QQ_1721727750327.png)



![img](GIt笔记.assets/9ef718d451efcc8052d4d5022a577368.png)

![img](GIt笔记.assets/QQ_1721727853283.png)

![img](GIt笔记.assets/QQ_1721727864342.png)

![img](GIt笔记.assets/QQ_1721727879854.png)

如果你是第一次创建SSH密钥

而且在创建密钥的时候也没有修改过默认的文件名的话

### SSH密钥的配置到这里就完成了

那如果你也像我一样

刚刚指定了一个新的文件名

那么还需要增加一步配置

![img](GIt笔记.assets/e6e7805c1199044f1dc7f57f6f2ec13e.png)

![img](GIt笔记.assets/QQ_1721728425527.png)

### 3、克隆远程仓库：git clone   github链接

![img](GIt笔记.assets/QQ_1721728470414.png)

![img](GIt笔记.assets/QQ_1721728528286.png)

![img](GIt笔记.assets/QQ_1721728561351.png)

克隆成功

### 4、远程仓库与本地仓库的关系

我们从第一节课就了解到，Git这是一种分布式的版本控制系统，本地仓库和远程仓库是两个仓库。他们之间是相互独立的。我们可以在本地仓库中做任何修改。但是，这些修改并不会影响到远程仓库。同样，远程仓库的修改影响到我们本地仓库。因此，我们需要一种机制来同步本地仓库和远程仓库的修改内容。让他们的状态保持一致，那这个同步的过程就涉及到了Git中两个新的命令。

#### 5、push：推送到远程仓库

#### 6、pull：拉取到本地仓库

这两个命令的含义和他的名字一样，非常形象，push表示推送，pull并表示拉取。push就是把本地仓库的修改推送给远程仓库。pull，就是把远程仓库的修改拉取到本地仓库

![img](GIt笔记.assets/QQ_1721729975400.png)

### 推送仓库：git push

![img](GIt笔记.assets/QQ_1721731176707.png)