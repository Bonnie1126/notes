# 1. Git 概念

## 1.1本地Git 中的三个区域

工作区:处理工作的区域,modified 表示修改了文件,还没有放到暂存区

暂存区:已完成的工作的临时存放区域,staged,已放到了暂存区

Git 仓库:最终的存放区域,commited 已放到了仓库  

## 1.2 Git工作流程

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=YjhlNDViYzFhODNiMTNhOTViZjk3YzNhYTVkZjI4ZTZfQzBwQ3VaVFViMHF3dTJzTG9SdzRQNTdkV2J0MG80NHBfVG9rZW46Ym94Y25wSElDSGxrd3pnUElRbFBRRFp1eVVjXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

clone（克隆）: 从远程仓库中克隆代码到本地仓库

checkout （检出）:从本地仓库中检出一个仓库分支然后进行修订

add（添加）: 在提交前先将代码提交到暂存区

commit（提交）: 提交到本地仓库。本地仓库中保存修改的各个历史版本

fetch (抓取) ： 从远程库，抓取到本地仓库，不进行任何的合并动作，一般操作比较少。

pull (拉取) ： 从远程库拉到本地库，自动进行合并(merge)，然后放到到工作区，相当于 fetch+merge

push（推送） : 修改完成后，需要和团队成员共享代码时，将代码推送到远程仓库

# 2. 本地git基础操作

## 2.1配置用户信息

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDhiMGI5Mzk0OWIzYmQwOWU3MjM2MGEyYWUyYjQ5MDRfenNBRlhETXRCR3dLQ2U5WGdESDRud1ZxQThyQk1vY2NfVG9rZW46Ym94Y251WVZMMmVGT1VwWk0wbHVPRnc3MU1iXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

## 2.2查看Git 的全局配置文件

在访达中 command+shift+.打开隐藏文件,在gaobo/.gitconfig

git config --list --global

## 2.3基础操作

### 1.使用帮助

git help 命令名字



### 2.将尚未进行版本控制的本地目录转换为 Git 仓库

打开一个文件

执行 git init 将当前目录转化为 git 仓库

工作区中文件的四种状态

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=NTY3Y2EzNDhjN2Q1ZGFlZjY5YWM1YWZmNjgxZjgxY2JfVUFVamVMM1ZMWUc2Q1NhZDE4UVd3U3RGQm1aMFhhcGVfVG9rZW46Ym94Y25aUjBwMERCUU9peENld3l5YXdDdGFnXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

git 操作的终极结果:让工作区的文件都处于"未修改"状态,也就是工作区的文件和仓库的文件保持一致

### 3.检查文件所处的状态

git status(--short)

### 4.跟踪新文件

git add 文件名 ,将会把这个文件提交到暂存区中

### 5.提交更新

现在暂存区已经有一个文件,等待被提交到git仓库中进行保存.

git commit -m"自定义提交信息"

### 6.对已提交的文件进行修改

目前,已经有一个文件被git跟踪,且工作区和git仓库中的该文件内容保持一致

如果修改该文件内容,状态是红色的modified,git status中Changes not staged for commit: -s是红色的M

表示修改了但是没放到暂存区

- git add 文件名将它放到暂存区 -s是绿色的M

- git commit -m "消息"   将暂存区中的文件提交到git仓库

### 7.撤销对文件的修改

指的是把工作区对应文件的修改,还原成git仓库中所保存的版本

操作的结果:所有修改会丢失,且无法恢复!危险性比较高,谨慎操作

git checkout -- 文件名, 撤销对该文件的所有修改

### 8.向暂存区中一次性添加多个文件

一次性将所有的新增和修改过的文件加入到暂存区

git add .

### 9.取消已暂存的文件

git reset HEAD 文件名(.)

### 10.跳过使用暂存区

git commit -a -m "提交描述消息"

### 11.git仓库移除文件

- 从git仓库和工作区同时移除

git rm -f 文件名

- 只从git中移除,工作区中仍保留

git rm --cached 文件名

### 12.git的忽略文件

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=ZGU3ZmEyNTdmNWI1OGVjMDYzZTEyNzRlZDdhMGQ5ZTBfQUNJWjdTdDhHVkdJbE5pT0VQdEZ6bzBrcm14RnlOVXFfVG9rZW46Ym94Y25ZM3BRb3lBWkZMT1IzZ0xiaG1LSWdoXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=NmVkYWM1ZjI5N2NhMzViOWIwMDc1MGYzNjIzYzE1M2VfdFYxN1JXRVZHME9VZWUzRTEybVpqQkJXTk1DTDJWdG1fVG9rZW46Ym94Y25KZkFKeDhXeGN6S0M2SzhnVFhIdUhiXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=YmU4YzEzZTIyZTRjOWMwZTQ2YTJlM2Q4OGNlM2RkZmNfTVJOUExBOWhvV0N0MHNmamptdVpKNGdTaFFBU3IwVE9fVG9rZW46Ym94Y25tWTkxWk9aMW9aQWhvb09OYkl1T2xmXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

### 12.查看提交历史

![img](https://s8j25z27ez.feishu.cn/space/api/box/stream/download/asynccode/?code=OTUxOTk2MjA5OTI1ZmM5YzAzOTc1OTI3ZTFmMGY3NjJfMnFDeVV5a1M1VkQ3RG05QTZlam1YZ2hUazVYNXNyTlJfVG9rZW46Ym94Y25va0Fqb2V5MW5jUmNCTGQ1R0xidDRnXzE2NjEyMzA1NzM6MTY2MTIzNDE3M19WNA)

### 14.回退到历史版本

- git log 把历史展示出来

- git reset --hard  提交ID

- git reflog 切换回旧版本中,仍然展示所有提交历史

# 3. 远程Git操作

## 3.1从其他服务器克隆一个已存在的 Git 仓库

### 1.Github

开源项目托管平台

### 2.两种访问远程仓库的方式

1. #### HTTPS:零配置,每次访问仓库,都要重复输入账号和密码

- 基于https将本地仓库上传到Github

复制https方式的第二个代码块

- 本地仓库的修改传到远程仓库

本地:

git add

git commit -m

远程:

git push

2. #### SSH:需要额外配置,配置成功后,则不需要每次输入账号和密码,还能实现加密数据传输,推荐

- 生成 SSH key

id_ras(私钥文件,存放于客户端的电脑中)

id_ras.pub(公钥文件,需要配置在Github中)

 ssh-keygen -t rsa -b 4096 -C"bonnie_1126@163.com"

连续三次回车

可在gaobo/.ssh目录中生成id_ras 和 id_ras.pub

- 配置SSH Key

打开本地的id_rsa.pub 复制

Github中 Setting-SSH and GPG keys- New SSH key

- 检测Github的SSH Key是否配置成功

ssh -T git@github.com

- 本地仓库上传到远程

复制Github上新建repository时的SSH方式下的代码

## 3.2克隆远程仓库

git clone 远程仓库地址

## 3.3分支的概念

在进行多人协作开发的时候,为了防止互相干扰,每个开发者都在自己的分支上进行开发,之后合并到master分支当中,不允许程序员在master分支当中修改代码

### 1.master 主分支

用来保存和记录整个项目已完成的功能代码

### 2.功能分支

用来专门开发新功能的分支,它是临时从master主分支上分叉出来的,当新功能开发且测试完毕后,最终需要合并到master主分支上

### 3.分支的相关操作

#### 查看git仓库中的所有分支列表

git branch

*是当前所在的分支

#### 创建新分支

git branch 分支名称

可以基于当前的分支,创建一个新分支,新分支中的代码和当前分支完全一样

#### 切换分支

git checkout 分支名称

#### 分支的快速创建和切换

git checkout -b 分支名称 

#### 合并分支

先切换到主分支上

git checkout master

在master分支上合并某分支

git merge 分支名称

#### 删除分支

git branch -d 分支名称

#### 遇到冲突时的分之合并

如果在两个不同的分支中,对同一个文件进行了不同的修改,Git就没办法干净的合并他们.此时我们需要打开这些包含冲突的文件然后手动解决冲突 

merge之后会展示出错误消息

这时回到源文件中有四个选项:采用当前的更改 采用传入的更改 保留双方的更改 比较更改 手动选择后

进行add 和 commit

#### 第一次将本地分支推送到远程仓库

git push -u 远程仓库的别名 本地分支名称:远程分支名称

如果希望远程分支的名称和本地分支名称保持一致,只写本地分支名称就好了

后续推送不需要带u了

#### 查看远程仓库中的分支列表

git remote show 远程仓库别名

#### 跟踪分支

指的是从远程分支上下载到本地仓库

git checkout 远程分支名

分支名在本地重命名

git checkout -b 本地分支名 远程仓库名/远程分支名

#### 拉取远程分支代码

git pull 

从远程仓库拉取当前分支的最新代码,保持当前分支的代码和远程分支代码一致

#### 删除远程分支代码

git push 远程仓库名称 --delete 远程分支名称

# 4.命令大汇总

| 命令                                                 | 含义                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| git init                                             | 初始化本地仓库                                               |
| git help 命令                                        | 获取命令的帮助                                               |
| git status(-s)                                       | 查看每个文件的所处状态                                       |
| git add 文件名                                       | (1) 跟踪文件(2) 把已跟踪/已修改的文件放到暂存区(3) 把有冲突的文件标记为已解决状态 |
| git add .                                            | 新增的和修改过的都添加到暂存区                               |
| git reset HEAD 要移除的文件名(.)                     | 从暂存区中移除对应文件                                       |
| git commit -m                                        | 暂存区的内容提交到git仓库中                                  |
| git commit -a -m "提交描述消息"                      | 跳过暂存区,直接把已跟踪的文件的文件提交到git仓库             |
| git checkout -- 文件名                               | 用git仓库中的覆盖当前工作区的                                |
| git rm -f 文件名                                     | 移除git仓库中的文件,移除工作区对应                           |
| git rm --cached 文件名                               | 移除git仓库中的文件,工作区保留                               |
| git log -数字                                        | 显示提交历史几条                                             |
| git reflog                                           | 切换回旧版本中,仍然展示所有提交历史                          |
| git reset --hard  提交ID                             | 返回指定版本                                                 |
| git branch                                           | 查看分支列表                                                 |
| git branch 分支名称                                  | 创建新的分支                                                 |
| git checkout 分支名称                                | 切换分支                                                     |
| git checkout -b 分支名称                             | 创建并切换分支                                               |
| git merge 分支名称                                   | 合并分支                                                     |
| git branch -d 分支名称                               | 删除分支                                                     |
| git clone 远程仓库地址                               | 克隆远程仓库                                                 |
| git push -u 远程仓库的别名 本地分支名称:远程分支名称 | 第一次本地仓库的分支 推送到远程仓库后续就不需要-u了          |
| git remote show 远程仓库别名                         | 查看远程仓库的分支                                           |
| git checkout 远程分支名                              | 远程分支下载到本地仓库,分支名一致                            |
| git pull                                             | 从远程仓库上拉取当前分支最新代码                             |
| git push 远程仓库名称 --delete 远程分支名称          | 删除远程分支 ****                                            |