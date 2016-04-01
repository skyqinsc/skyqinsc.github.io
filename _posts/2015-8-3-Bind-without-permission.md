---
layout: post
title: Bind：Bind Without Permission
categories: Linux
tags: Linxu网络编程

---

*基于linux平台服务器端编程，权限问题着实让人头疼，nobody进程为甚没有权限*

###Bind：No Permission ？ WHY！！！

FTP服务器实现：nobody进程+服务进程来完成控制连接和数据连接全过程，nobody进程负责解决权限问题（这里不用root进程，自然是安全考虑！）

普通用户无权限绑定1024一下的特权端口

对于uid大于0的用户，操作前会进行有效用户权限的检查，而root用户之间pass内核检测！

进程权限：

* ruid(实际用户id： real userid)、
* euid(有效用户用户:effective  userid)
* suid(保存用户id:saved userid)
* fuid(文件系统用户id)

**而实际检测是uid**

{% highlight c linenos %}

int capset(cap_user_header_t hdrp, const cap_user_data_t datap){
	return syscall(__NR_capset,hdrp,datap);
}

void get_privilege(){
	//root -> nobody
	struct passwd *pw = getpwnam("nobody");
	if(pw == NULL) return;
	if(setegid(pw->pw_gid) < 0) ERR_EXIT("setegid");
	if(seteuid(pw->pw_uid) < 0) ERR_EXIT("seteuid");
	//add capability
	struct __user_cap_header_struct cap_header;
	struct __user_cap_data_struct cap_data;
	memset(&cap_header, 0 ,sizeof(cap_header));
	memset(&cap_data, 0, sizeof(cap_data));
	
	cap_header.version = _LINUX_CAPABILITY_VERSION_1; //x64
	cap_header.pid = 0;

	__u32 cap_mask = 0;
	cap_mask |= (1 << CAP_NET_BIND_SERVICE);
	cap_data.effective = cap_data.permitted = cap_mask;
	cap_data.inheritable = 0;
	//end_add
	capset(&cap_header, &cap_data);
}
{% endhighlight %}
