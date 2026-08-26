```bash
git init #初始化本地仓库
git status #看状态

##从工作区放到暂存区  状态红色未加到暂区
git add .
git add 文件名字

##暂存区提交到本地仓库  绿色在暂存区 但是未加到本地仓库
git commit -m "操作信息" 文件名 #不加默认全部

git diff 文件名 #不加表示所有  工作区和暂存区代码比较
git diff HEAD 文件名  #不加表示所有  工作区和本地仓库当前版本比较
git diff --cached 文件名 #暂存区和本地库最新提交版本的差别

##########版本管理########
#q退出日志
git reflog  #查看 HEAD 指针移动记录  项目版本记录用于版本穿梭
git reflog -n #前n个
git log		#项目版本信息

git reset --hard 版本号 #版本穿梭

#########删除文件#######
#方法一
rm 文件名       #	删除工作区
git add 文件名		# 暂存区
git commit -m "删除xx" 

#方法二
git rm 文件名  #删除后需要提交 工作区：删除文件 暂存区：记录删除
git commit -m "删除xx"


#########分支#########
git branch xx #创建分支名字
git checkout xx #切换分支
git switch xx #新版切换

git checkout -b develop
git switch -c develop    #创建并切换

git switch -c feature/login develop #创建并切换 从 develop 分支复制出一个新的 feature/login 分支，并切换过去。
git checkout -b feature/login develop


git branch #查看分支  -r查看远程 -a查看所有 -v查看本地分支的详细信息（最近一次提交）
git branch -d xx #删除已经合并分支
git branch -D xx #强制删除

git merge xx #在master中 合并xx分支进来


#########远程仓库### 远程仓库别名：origin#####
git remote #查看远程仓库名称 -v详细信息显示

##添加远程仓库
git init
git remote add origin 仓库地址 #这个时候就是起远程别名

git remote set -url origin new仓库地址 #修改远程仓库地址

git remote rm origin #删除远程仓库 rm = remove

git clone 地址  xx#加后缀表示拉下来换个名字 不加默认

git push -u origin master #第一次推送 -u 设置 upstream（上游分支）

git fetch origin #下载远程最新提交，但不会合并到当前分支。
git merge origin/master #需要手动合并

git pull #等于上面两步


###密钥#####
ls ~/.ssh
ssh-keygen -t ed25519 -C"邮箱" #一直回车
cat ~/.ssh/id_ed25519.pub #复制粘贴到云端
```

