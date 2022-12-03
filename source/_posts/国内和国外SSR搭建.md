---
title: 国内外SSR搭建
date: 2022-12-1
categories:
- VPN
tags:
- SSR
- VPN
---

人在国内时，经常需要访问Yotube和Netflix观看视频，人在国外时，经常需要访问网易云音乐和QQ音乐等听歌，翻墙进墙不易，且行且珍惜。

<!-- more -->

`说明：本教程参考自一灯不是和尚的文章，有雷同之处属于正常，此文仅为个人搭建SSR的记录过程，不做任何建议。`

[参考文章地址](https://iyideng.net/black-technology/cgfw/shadowsocksr-ssr-server-building-and-using-tutorial.html)

#### 云服务器购买
在网上大部分人都告诉你，先购买VPS服务器，很多人比较奇怪，VPS服务器跟国内的云服务器有什么区别呢。其实他俩是一个东西，都是虚拟服务器，只是外国人叫VPS服务器，中国人叫云服务器。

- 国外VPS服务器推荐：[Vultr](https://www.vultr.com/)，在优质国外VPS服务商中，Vultr是性价比最高、最值得推荐的一家。

- 国内云服务器推荐：[腾讯云](https://cloud.tencent.com/act/pro/seckill_season)，[Ucloud](https://www.ucloud.cn/site/active/uhost.html)

- Windows使用Xshell连接VPS服务器，Mac使用iTerm进行连接。


#### SSR安装部署

- 安装`wget`依赖包(根据主机系统选择)

      yum -y install wget         # CentOS
      sudo apt-get install wget   # Debian/Ubuntu

- 安装`Curl`依赖包(根据主机系统选择)

      yum update -y && yum install curl -y            # CentOS/Fedora
      apt-get update -y && apt-get install curl -y    # Debian/Ubuntu

- 如果遇到权限问题，可使用命令`sudo su - root`，切换成root权限。

- SSR一键搭建脚本

  这里使用的是[逗比大神(ToyoDAdoubi)](https://github.com/ToyoDAdoubi/doubi#ssrsh)的SSR一键搭建脚本，因为全中文界面，操作更加简单方便。

      wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh

  安装完毕之后，参数全部默认即可，配置完成后会显示当前的SSR服务器和地址等，复制地址到客户端就可以使用了。


- 开启BBR加速

  安装`BBR`一键加速后速度会更快。BBR的好处就是可以套Cloudflare的免费CDN，更好地保护VPS的真实IP地址，而且免费使用CDN流量，极大地节省了带宽流量。

      cd /usr/src && wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh


#### 客户端使用

个人使用的是iPhone手机，所以用了`Potatso`客户端。直接复制ssr协议地址到postatso添加服务器就可以了。

ip检测：https://www.whatismyip.com.tw
