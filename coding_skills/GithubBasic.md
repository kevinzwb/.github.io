# 下载安装Git
打开终端，输入git。如没有安装，输入``` sudo apt-get install git```安装Git。

#配置
配置前检查.ssh文件夹（直接搜索该文件夹）下的known_hosts(如果有，请删除）
配置用户名和邮箱
``` 
$ git config user.name "Your Name"  
$ git config user.email "email@example.com"  
``` 

## 建立本地git仓库
- 在本地建立
``` 
$ cd /Users/mac/Desktop/kevinzwb/kevinzwb.github.io
$ git init 
$ git add .
$ git commit -m "添加你的注释"

``` 

- 从github上复制
``` 
$  git clone  https://github.com/kevinzwb/kevinzwb.github.io
``` 

# 上传代码到远程库
```
$ git remote add origin https://github.com/kevinzwb/kevinzwb.github.io
$ git pull origin master  
$ git push origin master  
```

## 本地远程同步
```
$  git commit -m 'commit content'
$  git pull origin master  
$  git push origin master  
$  git status
```
