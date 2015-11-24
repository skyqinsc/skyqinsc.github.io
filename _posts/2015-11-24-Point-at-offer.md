---
layout: post
title: 剑指offer练习
categories: algorithm
tags: Point_at_offer

---

### 记录剑指offer编程练习

[《剑指offer》代码库](https://github.com/skyqinsc/Point-at-offer)

* [1.二维数组中的查找](https://github.com/skyqinsc/Point-at-offer/blob/master/1.%E4%BA%8C%E7%BB%B4%E6%95%B0%E7%BB%84%E4%B8%AD%E7%9A%84%E6%9F%A5%E6%89%BE.cc)
* [2.替换空格](https://github.com/skyqinsc/Point-at-offer/blob/master/2.%E6%9B%BF%E6%8D%A2%E7%A9%BA%E6%A0%BC.cc)
* [3.从尾到头打印链表](https://github.com/skyqinsc/Point-at-offer/blob/master/3.%E5%80%92%E5%BA%8F%E6%89%93%E5%8D%B0%E9%93%BE%E8%A1%A8.cc)
* [4.重建二叉树](https://github.com/skyqinsc/Point-at-offer/blob/master/4.%E9%87%8D%E5%BB%BA%E4%BA%8C%E5%8F%89%E6%A0%91.cc)
* [5.用两个栈实现队列](https://github.com/skyqinsc/Point-at-offer/blob/master/5.%E7%94%A8%E4%B8%A4%E4%B8%AA%E6%A0%88%E5%AE%9E%E7%8E%B0%E9%98%9F%E5%88%97.cc)
* [6.旋数组的最小数字](https://github.com/skyqinsc/Point-at-offer/blob/master/6.%E6%97%8B%E8%BD%AC%E6%95%B0%E7%BB%84%E7%9A%84%E6%9C%80%E5%B0%8F%E6%95%B0%E5%AD%97.cc)
* [7.斐波那契数列](https://github.com/skyqinsc/Point-at-offer/blob/master/7_8_9.cc)
* [8.跳台阶](https://github.com/skyqinsc/Point-at-offer/blob/master/7_8_9.cc)
* [9.变态跳台阶](https://github.com/skyqinsc/Point-at-offer/blob/master/7_8_9.cc)
* [10.矩形覆盖](https://github.com/skyqinsc/Point-at-offer/blob/master/10.%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0%E5%88%97.py)
* [11.二进制中1的个数](#11)

---

<h4 id="11">11.二进制中1的个数</h4>

Pro:输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。

感觉还是比较有意思，如果是正整数自然好求，这里提供两种方法：

{% highlight c linenos %}
//solution A:
int solveA(int x){
    int ret=0;
    while(x){
        if(x%2==1) ret++;
        x/=2;
    }
    return ret;
}
//Sloution ex_A:
int EX_solveA(int x){
    int ret;
    while(x){
        if(x&1) ret++;
        x>>=1;
    }
    return ret;
}
{% endhighlight c %}

当然，上面的方法是有问题的，对于正整数自然是没有问题，但对于负数，符号位会自动补 1，例如 0X80000000 右移一位，是0Xc0000000，而不是0x40000000；

The correct solution：测试法
{% highlight c linenos %}
//Solution C
int solveC(int x){
    unsigned p=1,ret=0; // 此处一定要是unsigned，可以思考下Why。
    while(p){
        if(x&p) ret++;
        p<<=1;
    }
    return ret;
}
{% endhighlight c %}

下面提供一个，第一次get到的方法
{% highlight cpp linenos %}
//Solution D
int solveD(int x){
    int ret=0;
    while(x){
        ret++;
        x=x&(x-1);
    }
    return ret;
}
{% endhighlight cpp %}

说明：x-1,相当于把x数最右边的‘1’，和其右边的位全部取反，然后和x进行AND操作，相当于讲最右边的‘1’置为‘0’。

** \^_^这个方法可以一步判断一个正整数，是不是2的整数次幂**

---


### END