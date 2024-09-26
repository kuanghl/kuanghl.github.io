---
title: chirpy update
author: kuang_hl 
date: 2023-11-23 12:39:00 +0800
categories: [blogs]
tags: [bolgs,jekyll,git]
comments: true

# 其他还有：
description: this is a chirpy update. # 描述
toc: true # 打开目录
math: true # 加载数学功能
mermaid: true # 启用Mermaid
pin: true # 置顶帖子
---

- Upgrade the fork.
  
```shell
# 0.备份master分支
# 1.创建和切换分支master_copy
# 2.链接远端分叉仓库
# 3.并采集远端仓库信息到当前分支
# 4.基于远端分支创建新分支chirpy
# 5.远端仓库初始化
# 6.对比两个分支差异部分
# 7.对比两个分支具体文件的详细差异
# 8.切换成master分支
git checkout -b master_backup
git checkout -b master_copy
git remote add origin_chirpy git@github.com:cotes2020/jekyll-theme-chirpy.git
git fetch origin_chirpy
git checkout -b chirpy origin_chirpy/master
bash tools/init #  7.1.1 error
git diff master chirpy --stat
git diff master chirpy _config.yml
git checkout master

# 拷贝出关键文件
cp _config.yml ../
cp -r _posts ../
cp -r .github ../

# 1.切换成远端分支来源chirpy
# 2.移除远端分支
# 3.将文件考回覆盖
git checkout chirpy
git remote remove origin_chirpy
cp ../_config.yml .
cp -r ../_posts .
cp -r ../.github .
sudo rm -rf ../_config.yml
sudo rm -rf ../_posts
sudo rm -rf ../.github
git add .
git commit -m 'update chirpy'
git branch -d master
git checkout -b master
git push -f origin master

# 合并chirpy分支到当前分支,如果有冲突保留chirpy更改
git merge -X theirs chirpy --allow-unrelated-histories
# 合并chirpy分支到当前分支,如果有冲突保留当前分支更改
git merge -X ours chirpy --allow-unrelated-histories

# assets/lib commit id
97d95fd
```