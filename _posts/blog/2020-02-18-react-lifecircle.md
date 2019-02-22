---
layout: post
title: React生命周期
categories: React
description: 学习react过程中记录
keywords: react， note
---
### WHAT 
1. 生命周期函数是组件在某个时期自动调用执行的函数
2. constructor不算是生命周期函数。在组件创建的时刻被调用

### HOW
![生命周期图片](/images/life_circle.png)
1. initialization -> 挂载(Mounting) -> Updation -> Unmounting 
 
#### initialization: setup pros and state
#### Mounting: componentsWillMout -> render -> componentsDidMount
#### updation : componentsWillReceiveProps -> shouldComponentsUpdate -> componentsWillUpdate -> render -> componentsDidUpdate 
#### ummounting: componentWillUnmount

### WHEN
