---
layout: '../../layouts/MarkdownPost.astro'
title: 'Ubuntu安装NVIDIA驱动浓缩极简方法'
pubDate: 2023-04-20
description: ''
author: 'ion'
cover:
    url: 'https://img.loxx.cn/i/2023/04/20/j53u07.png'
    square: 'https://img.loxx.cn/i/2023/04/20/j53u07.png'
    alt: 'cover'
tags: ["Linux", "学习", "NVIDIA", "显卡", "驱动"]
theme: 'light'
featured: true
---

> 适用于台式机新装Ubuntu18.04、20.04、22.04系统，不用思考，直接复制粘贴代码！

```shell
sudo apt update #更新软件列表
sudo apt install gcc g++ make cmake #安装必要依赖
sudo vi /etc/modprobe.d/blacklist.conf #禁用nouveau，末尾添加如下两⾏命令保存

blacklist nouveau
options nouveau modeset=0

sudo update-initramfs -u #更新
reboot #重启电脑

lsmod | grep nouveau #检查，输入之后无输入即可

sudo init 3 #进入命令行界面
sudo chmod +X NVIDIA-Linux-x86_64-450.203.08.run #给你下载的驱动赋予权限，才可进行安装
sudo ./NVIDIA-Linux-x86_64-450.203.08.run -no-opengl-files #安装
reboot #重启即可
```