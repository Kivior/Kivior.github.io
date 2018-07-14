---
layout: post
title:  "Neural Style"
image: ''
date:   2017-09-02 00:00:00
tags:
- tensorflow
description: ''
categories:
- CS 
---


### 一、TensorFlow Windows下安装

- 我选择的是Anaconda的安装方法，他会自动安装Python环境，我用的是64位的Anaconda3 4.1.0，Python3.5.1
- 之后安装TensorFlow
- >Pip install tensorflow
- or
- >Pip install tensorflow-gpu
- pip可能需要更新
- 下的可能比较慢，也可以去github上clone一个。
- 因为我有N卡，所以CPU版本和GPU版本都试了一下。GPU版本需要安装CUDA8和cuDnn库，库文件放在CUDA8的安装目录下，而且需要继续添加环境变量。


### 二、neural-style

- neural-style是一个风格学习项目，好像是后来搬到TensorFlow上的。
- [项目链接](https://github.com/anishathalye/neural-style)
- neural-style依赖VGG19的深度学习库（Pre-trained VGG network 在项目主页有提供下载）[VGG19主页](http://www.vlfeat.org/matconvnet/pretrained/#downloading-the-pre-trained-models)
- 之前GPU版本的环境变量一直配置不好，所以最后用了CPU版本。

- >python neural_style.py --content /content file/ --styles /style file/ --output /output file/

- 在项目下填入训练风格输出文件等就OK了

![image](https://raw.githubusercontent.com/Kivior/kivior.github.io/master/img/TF-ns.jpg)

- 我用蒙娜丽莎做风格样本学习，在对梦露做风格处理，看上去效果一般，也许调教一下小参数会更好，但是笔记本的低压U在iterations 设为 1000 时跑了6个小时emmm...
 
