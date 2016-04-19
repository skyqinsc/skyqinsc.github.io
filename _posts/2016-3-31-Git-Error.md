---
layout: post
title: Git Error And Solution
categories: Linux
tags: Git

---

*小叙:一直使用Ubuntu物理机，但是由于学校课程安排，切换于Win/Linux间感到很累。最近重新配置了自己
的Linux开发环境，Centos 7的虚拟机后台运行，Win上使用Xshell客户端ssh连接服务器，使用很方便；据说
Xshell+Xftp是服务器端的神器!*

###这里主要记录下Git使用中遇到的Error和相应解决办法:

1. git在push的时候出现`insufficient permission for adding an object`错误
> No Permission ！对这一般是权限问题，
> 
> 这里需要修改owner的权限。你可以通过`ls -al`命令查看权限，
> 
> 比如：我发现.git/objets/下多个文件的owner是root，我qinsc用户自然git commit过程导致权限不足；
>
> **解决办法：**`chown -R qinsc .git/objects`递归改变权限


