---
layout: post
title: 剑指offer练习
categories： algorithm
tags： Point at offer

---

## 剑指offer练习

**Pro:[位运算] 二进制中‘1’的个数**
> 我想求正整数中‘1‘的个数，都会，看两个解法：
> {% highlight cpp linenos %}
>
//solution A:
int solveA(int x){
    int ret=0;
    while(x){
        if(x%2==1) ret++;
        x/=2;
    }
    return ret;
}
>
//Sloution ex_A:
int EX_solveA(int x){
    int ret;
    while(x){
        if(x&1) ret++;
        x>>=1;
    }
    return ret;
}
>
//上面的方法是有问题的，对于正整数自然是没有问题，但
//对于负数，符号位会自动补 1，例如 0X80000000 右移一
//位，是0Xc0000000，而不是0x40000000；
>
{% endhighlight cpp %}