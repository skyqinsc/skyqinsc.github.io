---
layout: post
title: Learning Python
categories: Python Tutorial
tags: python

---

*Just to take notes*

**Day one**


1. python中的build-in类型，int，float，string
2. python中的Control Flow：while,for,if elif..else
3. Lists（pop(),insert(),append()...)，slice([:]...)
4. python以缩进来代表作用域，so缩进一定要准确，不然会syntax error

一些不同的地方（As a c++ programer）：
{% highlight py %}
	for num if range(2,10):
    	for i in range(2,num):
        	if num%i==0:
            	print num,"=",i,"*",num/i
                break
        else:
        	print num,"is a prime"
{% endhighlight %}
上面的程序是没有错的，else此处就是loop的字句，当没有break时，else clause run！

