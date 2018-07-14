---
layout: post
title:  "关于重写 equals & hashCode"
image: ''
date:   2018-4-24 00:06:31
tags:
- JAVA
description: ''
categories:
- JAVA
---


Q:为啥重写equals？  
A:果不重写equals，那么比较的将是对象的引用是否指向同一块内存地址，重写之后目的是为了比较两个对象的value值是否相等。

Q:那hashCode呢？  
A:由于为了提高程序的效率才实现了hashcode方法，先进行hashcode的比较，如果不同，那没就不必在进行equals的比较了，这样就大大减少了equals比较的次数，这对比需要比较的数量很大的效率提高是很明显的. hash将对象数据根据该对象的特征使用特定的算法将其定义到一个地址上,只要就大大减少了equals的使用次数，执行效率就大大提高了。

Q:....   
A:如果重写了equals而未重写hashcode方法，可能就会出现两个没有关系的对象equals相同的(因为equal都是根据对象的特征进行重写的)，但hashcode确实不相同的.

Q:...   
A:假设两个对象，重写了其equals方法，其相等条件是属性相等，就返回true。如果不重写hashcode方法，其返回的依然是两个对象的内存地址值，必然不相等。这就出现了equals方法相等，但是hashcode不相等的情况(因为hash对比的是对象地址¿)。这不符合hashcode的规则。  
<br>
一个栗子  
```java
public class worker {
    private  int age;
    private String name;
    private double salary;
    public  worker(String name,int age,double salary){
        this.name=name;
        this.age=age;
        this.salary=salary;
    }

    //....省略封装
   
    @Override
    public int hashCode() {
        int result = 17;
        result = 31 * result + name.hashCode();  //String自带重写
        result = 31 * result + age;    
        result = 31 * result + (int)salary;
        return result;   //or return getName().hashCODE()
    }

    @Override
    public boolean equals(Object obj) {
        if(obj == this)
            return true;
        if(!(obj instanceof worker))
            return false;
        worker worker=(worker)obj;
        return worker.name==this.name;
    }
    //  public String toString() {return name+" "+age+" "+salary;}
}

public class WorkerMain {
    public static void main(String[] args) {
        List<worker> workerList =new Vector<>();
        worker zhang =new worker("zhang3",18,3000);
        worker li =new worker("li4",25,3500);
        worker wang =new worker("wang5",25,3200);       

        worker wang6 =new worker("wang5",25,3200);
        System.out.println(wang6.equals(wang));   //wang6&wang true

        worker wang7 =new worker("wang5",25,3200);
        Set<worker> workerHash=new HashSet<>();
        workerHash.add(wang6);
        System.out.println(workerHash.add(wang7));   //wang6&wang7 false

    }
}
```
