# git笔记

## 一、版本控制

> 优点：利于开发，提高效率

**版本控制功能**

- 协同修改--多人修改一个文件
- 数据备份--不仅保存当前状态还保存了历史提交状态
- 版本管理--不保存重复数据，以节约存储空间 svn：增量式管理，git:文件系统快照方式
- 权限控制--对团队外开发者贡献的代码进行审核（独有）
- 历史记录--将本地文件恢复到某一个历史状态
- 分支管理--多个小组同时工作

集中式版本控制工具:svn

分布式版本控制工具：git 



## 二、git简介

2005年，linux 用c语言开发了一个分布式版本系统控制系统：git

**git优势**

- 大部分操作在本地完成，不需要联网
- 完整性保证
- 尽可能添加数据而不是删除或修改数据
- 分支操作非常快捷流畅
- 与Linux命令全面兼容





## 三、git命令行操作

## **1.本地库操作**

### 1.1本地库初始化

​	**ll** ---当前目录下的所有资源

​	**ls -lA** ----当前目录下的隐藏资源

​	**ls -l|less**    "|" 管道符  用于实现文件列表的分页

​	**ll**   是会显示当前目录下的文档详细信息,是ls -l的缩写

​	**cd **退回/前进

​	**mkdir **  新建目录

​	**git init**  初始化一个空的仓库 

![1571573491787](C:\Users\26460\Desktop\学习文件\git.assets\git_init.png)

**pwd**



​	命令：**git add**

​	效果：

![1571582318934](C:\Users\26460\Desktop\学习文件\git.assets\1571582318934.png)

​	注意：**.git 目录中存放的是本地库相关的子目录和文件，不要删除，也不要胡乱修改**

### 1.2  设置签名 

​	**形式**

​		用户名：

​		email地址：

​	**作用**：区分不同开发人员的身份

​	**辨别**：这里设置的签名和登录远程库（代码托管中心）的 账号密码无关

​	**命令**：

​		项目级别/仓库级别：仅在当前本地库范围内有效      （保存在./.git/config文件下）

```
git congif user.name nxy
git config user.email 2646096926@qq.com
```

​		系统用户级别：登录当前操纵系统的用户范围         （保存在c:/user/26460/.gitcongif文件下）

```
git config -global user.name nxy
git config -global user.email 2646096926@qq.com
```

​		级别优先级：（就近原则）

​			项目级别/仓库级别**优先于**系统用户级别，二者都有时采用项目级别的签名

​			二者都没有是不允许的

### 1.3 git 的操作（与本地库操作）

#### 	1.3.1 提交

​	**git status**--- 工作区、暂存区的状态

​	**git add <file>**--添加到暂存区（红-->绿的转变）

​	**git rm --cached <file>**--删除暂存区中的文件

​	**git commit <file>**--提交到本地库

​	**git commit ”commit message“ <file>**--提交

​	**cat <file>** --查看文件

​	**vim编辑器  i键编辑  :wq退出**

​	**git checkout --<file>**   取消修改 

**创建文件以及添加到暂存区**

![1571734644971](git.assets\1571734644971.png)

![1571734774067](C:\Users\26460\Desktop\学习文件\git.assets\1571734774067.png)

**提交以及提交过后**

![1571735002489](C:\Users\26460\Desktop\学习文件\git.assets\1571735002489.png)

![1571735023370](C:\Users\26460\Desktop\学习文件\git.assets\1571735023370.png)

------

**修改文件提交**

![1571659615142](C:\Users\26460\Desktop\学习文件\git.assets\1571733703609.png)



#### 1.3.2 历史记录

**git log**

![1571660175918](C:\Users\26460\Desktop\学习文件\git.assets\1571735298398.png)

查看文件

![1571704546756](C:\Users\26460\Desktop\学习文件\git.assets\1571734400761.png)

编辑文件内容并提交到本地库

再次查看历史记录

![1571704647097](C:\Users\26460\Desktop\学习文件\git.assets\1571735336647.png)

##### ***多屏显示控制方式

- 空格向下翻页
- b 向上翻页
- q 退出

**历史记录多的话**

**git log --pretty=oneline**

![1571705069291](C:\Users\26460\Desktop\学习文件\git.assets\1571735384656.png)

**git log --oneline**

![1571705056211](C:\Users\26460\Desktop\学习文件\git.assets\1571735406702.png)

**git reflog**

![1571705011786](C:\Users\26460\Desktop\学习文件\git.assets\1571735433439.png)

head{1} 就是到某个版本需要移动一次

#### 1.3.3 版本的前进后退

![1571735835728](C:\Users\26460\Desktop\学习文件\git.assets\1571735835728.png)

基于HEAD指针进行版本移动

------



版本更改前的文件状态

![1571735695827](C:\Users\26460\Desktop\学习文件\git.assets\1571735695827.png)

 

版本退回后的文件内容

![1571708459612](C:\Users\26460\Desktop\学习文件\git.assets\1571735745375.png)

​	git reset --hard <HEAD^>     :  ^只能后退

![1571708956858](C:\Users\26460\Desktop\学习文件\git.assets\1571735790505.png)

​	git reset --hard <HEAD~n>   ：  ~只能后退  n表示后退n步

![1571735650638](C:\Users\26460\Desktop\学习文件\git.assets\1571735650638.png)

##### reset 的三个参数

​	soft 仅在本地库移动HEAD指针

​	mixed  在本地库移动HEAD指针 重置暂存区

​	hard   在本地库移动HEAD指针   重置暂存区  重置工作区

#### 1.3.4 删除文件找回

##### 删除文件

前提：删除前，文件存在时的状态提交到了本地区

![1571736094290](C:\Users\26460\Desktop\学习文件\git.assets\1571736094290.png)

```
rm <file name>
```

![1571736147888](C:\Users\26460\Desktop\学习文件\git.assets\1571736147888.png)

添加到暂存区并提交文件

![1571736216651](C:\Users\26460\Desktop\学习文件\git.assets\1571736216651.png)

![1571736301358](C:\Users\26460\Desktop\学习文件\git.assets\1571736301358.png)

回到版本即可找回文件

![1571736625298](C:\Users\26460\Desktop\学习文件\git.assets\1571736625298.png)

添加到暂存区的删除文件

git reset --hard <HEAD>

**总结：**

git reset --hard <HEAD>

- 删除操作已经提交到本地库的文件： 指针位置指向历史记录
- 删除操作尚未提交到本地库的文件：指针位置指向HEAD

#### 1.3.5 比较文件

**git diff <file name>**  将工作区的文件与暂存区的文件进行比较

![1571790730947](C:\Users\26460\Desktop\学习文件\git.assets\1571790730947.png)

**git diff (HEAD) <file name>**  将工作区的文件与本地库历史记录比较

![1571790710034](C:\Users\26460\Desktop\学习文件\git.assets\1571790710034.png)

**git diff** 不带文件名比较多个文件 

![1571790784852](C:\Users\26460\Desktop\学习文件\git.assets\1571790784852.png)

#### 1.3.6 分支操作

![1571792160985](C:\Users\26460\Desktop\学习文件\git.assets\1571792160985.png)

##### 	a.创建分支

​		git branch <分支名>  

##### 	**b.查看分支**

​		git branch -v

##### 	**c.切换分支**

​		git checkout <分支名>

##### 	**d合并分支**

​		**第一步**： 切换到接受修改的分支（被合并，增加新内容）上

​			git checkout <被合并分支名>

​		**第二步**：执行merge命令

​	 		git merge <有新内容分支名>

![1571793148035](C:\Users\26460\Desktop\学习文件\git.assets\1571793148035.png)

##### 	f.解决冲突（conflict）

​		两个分支都有修改的时候会产生冲突

​	![1571793686750](C:\Users\26460\Desktop\学习文件\git.assets\1571793686750.png)

![1571793913726](C:\Users\26460\Desktop\学习文件\git.assets\1571793913726.png)

![1571794123583](C:\Users\26460\Desktop\学习文件\git.assets\1571794123583.png)

vim demo.txt 

![1571794251162](C:\Users\26460\Desktop\学习文件\git.assets\1571794251162.png)

git status(可有可无)

![1571794457678](C:\Users\26460\Desktop\学习文件\git.assets\1571794457678.png)

添加暂存区

![1571794614971](C:\Users\26460\Desktop\学习文件\git.assets\1571794614971.png)

提交（注意：不要带文件名）

![1571794759528](C:\Users\26460\Desktop\学习文件\git.assets\1571794759528.png)

1. 编辑文件，删除特殊符号，保存退出

2. git add <file name>

3. git commit -m "日志信息"

   （注：此时commit一定不能带具体文件名）

## 2.远程库操作

创建本地库然后创建远程库

#### 2.1如何创建远程库（代码托管中心）

![1571795570128](C:\Users\26460\Desktop\学习文件\git.assets\1571795570128.png)

![1571796228849](C:\Users\26460\Desktop\学习文件\git.assets\1571796228849.png)

远程库创建完成

#### 2.2  本地库与远程库的操作

##### 2.2.1 连接远程库

复制地址

命令窗口保存地址

git remote -v   查看地址

![1571796699403](C:\Users\26460\Desktop\学习文件\git.assets\1571796699403.png)

git remote add <别名><地址>

##### 2.2.2 推送

git push <别名origin>分支名

![1571797976343](C:\Users\26460\Desktop\学习文件\git.assets\1571797976343.png)

（因为https 上传不成功而修改origin url为ssh）

**git push origin master**

上传成功

![1571798119883](C:\Users\26460\Desktop\学习文件\git.assets\1571798119883.png)

##### 克隆

git clone <地址>

**效果:**

1. 完整的把远程库下载到本地
2. 创建origin远程库地址别名
3. 初始化本地库

![1572915071956](C:\Users\26460\Desktop\学习文件\git.assets\1572915071956.png)

##### 2.2.3 邀请加入团队

##### 2.2.4 拉取

**pull== fetch+merge**

**git fetch origin master**

只下载不更改本地库的东西

**git merge  origin/master**

合并

##### 2.2.5 解决冲突

![1572916022567](C:\Users\26460\Desktop\学习文件\git.assets\1572916022567.png)

##### 2.2.6





## 四、git图形化界面操作





## 五、gitlab服务器环境搭建



