---
title: markdown books
author: kuang_hl 
date: 2023-11-23 12:39:00 +0800
categories: [blogs]
tags: [bolgs,books,git]
comments: true

# 其他还有：
description: this is a books tutorial. # 描述
toc: true # 打开目录
math: true # 加载数学功能
mermaid: true # 启用Mermaid
pin: true # 置顶帖子
---


- [ ] gitbook.
- [x] mkdocs.
  - 新建仓库，进入仓库配置`Setting --> Actions --> General --> Workflow permissions`读写权限。
  - 克隆项目[mkdocs-material-demo](https://github.com/kuanghl/mkdocs-material-demo.git)
  - 待仓库的GitHub Actions执行完毕后，进入仓库配置`Setting --> Pages --> Build and deployment`，选择`Deploy from a branch --> gh-pages --> Save`。
  - 仓库的GitHub Actions流程中查看部署的网址

```sh
pip install mkdocs-material
# pip install mkdocs-exporter
# pip3 install mkpdfs-mkdocs
# pip3 install mkdocs-macros-plugin
# pip3 install mdx_truly_sane_lists
# pip install WeasyPrint

# pip install mkdocs-awesome-pages-plugin
# pip install mkdocs-redirects
# pip install mkdocs-minify-plugin
# python -m playwright install
# python -m playwright install --with-deps
# pip install poetry

# test
mkdocs serve
mkdocs build
```

    
- [x] mdbooks.
  - 后续环境不需要再次安装，pdf导出网络端和本地端有区别。

```sh
sudo apt-get install cargo
cargo --version

cargo install mdbook
mdbook --version
# 临时
export PATH=/home/hongliangkuang/.cargo/bin:$PATH
# 永久对所有用户生效
sudo vim /etc/profile
# 永久对单个用户生效
sudo vim ~/.bashrc
# 文件中添加
export PATH="$PATH:/home/hongliangkuang/.cargo/bin"
export PATH="$PATH:$(pwd)/bin"
# 刷新环境变量
source /etc/profile
source ~/.bashrc
mdbook --version

mdbook init bookdir_name
mdbook serve --open

# 安装卸载google浏览器和snapd
sudo apt purge snapd
sudo apt install snapd
sudo snap install chromium
sudo snap remove chromium
sudo apt install chromium-browser
sudo apt remove chromium-browser
sudo apt purge chromium-browser

cargo install mdbook-katex
cargo install mdbook-admonish
mdbook-admonish install

# cargo install mdbook-pdf 失败，自行编译
git clone https://github.com/HollowMan6/mdbook-pdf.git
cargo build --release
cp -r ./target/release/mdbook-pdf /home/hongliangkuang/.cargo/bin
pip install mdbook-pdf-outline

cargo install mdbook-mermaid
mdbook-mermaid install
```

> 页面不刷新的情况: 按下Ctrl + F5刷新页面缓存。{: .prompt-danger }