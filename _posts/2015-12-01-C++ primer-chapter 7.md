---
layout: post
title: C++ primer 学习笔记(chapter 7)
categories: C++ Primer
tags: C++

---

###类与对象

**1.This指针**

total.isbn(),实际上编译器会把toatal的地址传给this指针;

this指针的类型：Sales_data *const this; 
this是一个顶层指针（即是它自己是个常量） 