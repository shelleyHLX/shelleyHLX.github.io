---
layout: post
title:  "Atom安装,ubuntu系统"
date:   2018-12-4
categories: software
tags: atom
---
* content
{:toc}


## 下载文件
网址: https://atom.io/

下载deb文件: atom-amd64.deb

## 安装
sudo dpkg -i atom-amd64.deb


## 过程如图

![image](http://shelleyHLX.github.io/assets/SoftwareInstall/atom-install.png)

## 使用VNC方式访问时，无法正常使用Atom

lxp3@nlp:~/下载$ Xlib:  extension "XInputExtension" missing on display ":10.0".<br />
Xlib:  extension "XInputExtension" missing on display ":10.0". <br >
Xlib:  extension "XInputExtension" missing on display ":10.0".

解决:
sudo cp /usr/lib/x86_64-linux-gnu/libxcb.so.1 /usr/share/atom/
cd /usr/share/atom
sudo sed -i 's/BIG-REQUESTS/_IG-REQUESTS/' libxcb.so.1
