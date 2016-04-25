---
layout: post
title: CentOS 网络配置
categories: Linux
tags: Network

---

*小叙:CentOS服务器配置网络出现bogon问题，进而引发网络的无法访问！*

这里贡献自己的eth0虚拟网卡的配置：

> `vim /etc/sysconfig/network-scripts/ifcfg-eth0`
>
>	DEVICE=eth0
	HWADDR=00:0C:29:82:07:12
	TYPE=Ethernet
	UUID=cb5caa1e-7309-4469-833b-c01cb809973b
	ONBOOT=yes
	NM_CONTROLLED=yes
	BOOTPROTO=static
	NETMASK=255.255.255.0
	IPADDR=192.168.79.3
	IPV6INIT=no
	IPV6_AUTOCONF=no
	GATEWAY=192.168.79.2
	DNS1=8.8.8.8
	DNS2=8.8.4.4
	DOMAIN=localhost.localdomain
