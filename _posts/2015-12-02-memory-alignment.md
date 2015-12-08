---
layout: post
title: struct|union 内存对齐详解
categories: C++ Primer
tags: C++

---

**对齐规则**

*----对于union和struct占用内存大小的探讨：*

* union:what is the definition of union？The whole members of union share the same memory in your computer！

* struct:struct is the same as set,including lots of data members in different types！

*（there is any syntax error？）*

++The main body:++

1. 结构体当前成员从其大小（或者其成员大小）的整数倍开始存；
2. 结构体作为成员：那么该结构体内部最大成员的整数倍开始存；
3. 结构体或联合体的大小，为其最大成员大小的整数倍，不足则补齐；

++some instances：++

{% highlight cpp %}

/*
    struct
*/
typedef struct A_{
	char str[3]; //0-2
    int a; //4-7
    float b; //8-11
    double c; //16-23
}A;

typedef struct B_{
	char str[5];//0-4
    A a;//8-31 ：：struct A_的最大成员8byte
    int a;//32-35
    short b;//36-37 [38-39补齐：：最大8byte all=6*8=48byte]
}B;

/*
    union
*/

union C_{
	int a;//int 4byte
    char b[10];//char 1byte
};// 12byte ::4byte的整数倍

union D_{
	double a; //int 8byte
    char b[10];//char 1byte
};//16byte::8byte的整数倍


{% endhighlight %}

++reslut of ex：++
![运行结果](/assets/images/memory-alignment.png)
