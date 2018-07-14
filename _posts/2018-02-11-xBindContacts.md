---
layout: post
title:  "xBindContacts"
image: ''
date:   2018-02-11 00:07:31
tags:
- UWP
description: ''
categories:
- CS 
---


  
DataBound 动态数据绑定  

需要有人告诉GridView 数据更新了 >.<  

```cpp
 //private List<Contact> Contacts;
 private ObservableCollection<Contact> Contacts;

ItemsSource="{x:Bind Contacts}  //ちょっと　UPDATE


   //Contacts = new List<Contact>();
            Contacts = new ObservableCollection<Contact>();

```
  
