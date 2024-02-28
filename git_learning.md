# 在本地创建一个文件夹用于同步远程的github仓库完整步骤
  
  需要满足该电脑已经与远程仓库建立SSH连接
  
### 1、创建一个文件夹，然后打开git bash，输入
```
git init
git clone git@...
```
其中git@为github仓库的ssh key
### 2、在git bash中输入
```
git remote rm origin
git remote add origin git@...
```
其中git@为github仓库的ssh key
### 3、可以使用指令来提交文件到远程仓库
```
git add file.name
git commit -m "introduction"
git push -u origin main
git push origin main
```