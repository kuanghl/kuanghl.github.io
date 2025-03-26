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
bash tools/init #  7.1.1 error所以以下更新需要配合build
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

- build.

#### windows

```sh
# https://mp.weixin.qq.com/s/XAj-3NGsAvmPfcYIasZ2fA
# https://jekyllrb.com/docs/installation/windows/
# https://rubyinstaller.org/downloads/
# https://nodejs.org/en/download/prebuilt-installer
# 1. 下载安装
Ruby+Devkit x.x.x-x64
MSYS2 and MINGW development toolchain
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/ # 更换中国源
gem install jekyll bundler wdm # 使用Powershell jekyll bundler
jekyll -v  # 验证
node-vx.x.x-x64.msi
node -v # 验证
npm -v # 验证
npm config set registry https://registry.npmmirror.com  # 切换淘宝源镜像

# 2. build
git clone git@github.com:cotes2020/jekyll-theme-chirpy.git
bundle
npm i 
npm run build # assets
# 从Gemfile中删除gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]
# 在_config.yml最后添加port: 4001
bundle exec jekyll s

# 3. new
#首先创建一个c:\work的目录，然后前往这个目录。
cd c:\work
#用jekyll初始化博客站点kukisama.github.io，在做这个操作之前，要提前用VScode将整个kukisama.github.io拉回来，也就是说，kukisama.github.io目录是实际存在的。
jekyll new kukisama.github.io
#前往这个目录
cd kukisama.github.io
#将这个目录变成可用的http站点，直接访问下面的地址即可看到实际效果
#http://localhost:4000
bundle exec jekyll serve

# 如果系统是Ruby 3.0.0，且发现服务器起不来，输入这条命令
# bundle 本身会在各种回显上进行提示，如果有报错，注意看下错误信息中关于bundle 的内容，按照提示可以修复错误。
bundle add webrick
#因为本身Jekyll是个代码生成器，修改MD并不是立刻映射到html文件上。
#可以用这条命令启动服务，这样文件被改变之后，会即刻刷新网页
bundle exec jekyll serve --livereload
```

#### ubuntu

```sh
# 1. install ruby3.3.5
sudo gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm list known
rvm install ruby-3.3.5
gem uninstall -i /home/kuanghl/.rvm/rubies/ruby-3.3.5/lib/ruby/gems/3.3.0 gem-wrappers

# 2. install node
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
source ~/.bashrc
nvm install 20.10.0
node -v
sudo apt-get install build-essential zlib1g-dev

# 3. install jekyll 
source ~/.rvm/scripts/rvm # 启动ruby
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/ # 切换中国源
gem sources -l
gem install jekyll bundler # sudo apt install jekyll

# 4. build jekyll-theme-chirpy
source ~/.rvm/scripts/rvm # 启动ruby
git clone git@github.com:cotes2020/jekyll-theme-chirpy.git
# 更改Gemfile的源为source "https://gems.ruby-china.com/"
bundle
git config  user.email "kuanghl1998@163.com"
git config  user.name "kuanghl"
npm config set proxy null
npm config set registry https://registry.npmmirror.com  # 切换淘宝源镜像
bash tools/init.sh
npm i && npm run build # assets
bundle exec jekyll s
# 在_config.yml最后添加port: 4001
sudo lsof -wni tcp:4000 # 将4000端口占用的进程重新配置一下其他端口

# 5. upgrade
# 拷贝_posts文件到初始化完成的jekyll-theme-chirpy
# 比对_config.yml和pages-deploy.yml,合并更改即可完成更新

# 6. new
jekyll new test.github.io
cd test.github.io
bundle install
bundle exec jekyll s
```
