# Git使用教程

## 第一章 理解git工作流程

### 1.1什么是git

Git 是一个免费和开源**分布式版本控制系统**，旨在以速度和效率处理从小型到非常大型项目的所有问题。Git易于学习，足迹很小，性能快闪电。它超越了SCM工具，如颠覆，CVS，Perforce，和ClearCase的功能，如便宜的本地分支，方便的中转区，和多个工作流程。

- 文件夹拷贝

- 本地版本控制

- 集中式版本控制

- 分布式版本控制

  

**git简单来理解**

- 开源免费软件
- 分布式
- 版本控制



### 1.2为什么要做控制版本

要保留之前所有的版本，以便回滚或修改



### 1.3安装git

详见：[Git - Downloads (git-scm.com)](https://git-scm.com/downloads)  官网



**Git三大区域原理**

1. 工作区

   进入该文件目录新增或修改，查询该目录状态，提示文件名变（红色）意思是暂未提交该文件。

2. 暂存区 

   在该目录提交某个或所有文件时，再次查询时文件名会变（绿色）意思是已存在暂存区。

3. 版本区

   发布该文件或所有文件时，再次查询该目录状态下显示暂未有文件可发布。



## 第二章 Git项目流程

### 2.1 Git的基本使用

想要让git对一个项目进行版本控制需要以下步骤：

- 进入该项的目录

点击鼠标右键 提示有 -- git Bash Here

注：如未安装git，先安装git

- 执行初始化命令

```
git init
```

- 查询管理目录下的文件状态

```
git status
注：新增的文件和修改过后的文件名称都是红色
```

- 管理指定文件提交（红变绿）

```
git add 文件名
git add .    （所有文件）
```

- 生成版本

```
git commit -m '描述信息'
```

- 查看版本历史记录

```
git log
```

- 把本地已提交的文件推到git线上仓库里

```
git push
```



### 2.2 Git添加与更改

#### 2.2.1 拓展新功能

```
git add //文件名称
git commit -m '描述信息' 
```

#### 2.2.2 新功能不被审核

git之版本回退：git reset

```
第一步：先查看版本历史记录
git log
注：输入命令git log后如何退出，输入q键会自动退出git log命令

第二步：回退到指定版本
git reset --hard commitId（通过git log可查看提交的commitId）

第三步：重新提交代码
git commit a.txt -m "重新提交"   
注：记得不要提交不想提交的文件哦

第四步：推到git仓库线上
git push

如果我们不小心误会把不想要的版本提交到push线上
执行 git reflog 即可查询处理代码丢失、恢复代码
第一步：执行 git reflog 查看操作日志
git reflog
第二步：查看对应的版本号,就可以恢复到任意版本
git reset --hard "<commit ID>"
```



## 第三章 Git分支

### 3.1 什么是分支

概述：分支可以给使用者提供多个环境，意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线。

### 3.2 分支流程图

![](E:\SecondBrother\project\Git\GitUse\img\git分支流程图.jpg)



**Master分支：**

用于版本发布，每一个节点都应该是可发布版本；

每次合并到master时，都应添加tag标签作为版本号；

严禁从develop分支或feature分支直接合并到master分支；

 

**Develop分支：**

作为开发的主分支始终存在；

当有功能分支完成，应尽早合如develop分支，开发人员应daily拉取远端develop分支，尽早解决冲突代码；

 

**Release分支：**

发布新版本前的准备分支，从develop分支创建，创建后develop的更新不再合并到此release分支中， 该分枝只进行bug修复和文档修改，待版本稳定后，将该分支合并到master和develop分支，并删除该分支；

 

**Feature分支：**

功能开发分支，从develop分支创建，主要是在本地开发使用的分支，开发周期不宜过长，应尽早处理与服务器的冲突；

功能完成后，合并到develop分支，并删除该分支；

当存在比较独立或长期或容易与其他任务产生大的冲突的任务，建议check出feature分支，独立开发；

 

**Hotfix分支：**

生产环境紧急bug修复分支，从master分支创建，完成bug修改后，合并到master和develop分支，并删除该分支；



### 3.3 分支命令行使用

```
--清屏
clear

--在远程仓库创建新分支在本地更新
git pull

--查看分支
git branch

--创建分支
git branch <分支名>

--切换分支
git checkout <分支名>

--把本地新分支推送远程仓库
git push -u origin <分支名>
注：需要切换到该分支才能执行以上命令

--合并分支
git merge <分支名>
注：合并之后需要git push 才能推送到远程仓库

--删除本地分支
git branch -d <分支名>

--删除本地分支如何恢复分支
1、切换回master分支
2、git reflog --date=iso
3、git checkout -b <分支名> <commit ID> 

--删除远程分支
git push origin --delete <分支名>
注：删除本地分支不会影响到远程分支
```

