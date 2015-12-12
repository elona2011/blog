title: Git笔记
date: 2015-03-21 12:31:49
tags: [git]
categories:
      - 版本控制
---

# 添加SSH keys
https://help.github.com/articles/generating-ssh-keys/

## 远程库克隆
```
git clone <SSH clone URL>
```
<SSH clone URL> 在github相应仓库首页右侧点击SSH clone URL的复制按钮

## git stage
同git add，文件快照

## git commit
```
git commit -a
```
递交所有内容

## 提交到远程库
```
git push origin master
```

当前目录下git init
```git add .```
```git status``` 查看暂存区