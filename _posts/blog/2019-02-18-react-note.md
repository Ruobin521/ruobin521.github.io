---
layout: post
title: React笔记
categories: React
description: 学习react过程中记录
keywords: react， note
---
### WHAT 
1. registerServiceWorker是什么，如何运行的
2. 在jsx中使用方法，为什么要bind(this),以及在jsx中bind为什么会影响性能？
3. this.setState通过函数异步更新的原理以及注意事项,prevState的存在
4. 在循环渲染中用index做key值为什么不靠谱，应该怎么处理


### Props,State,Render
 1. 当组件的state或者props发生变化的时候，render函数就会重新执行
 2. 当父组件的render重新执行时，他的子组件的render也会被执行一次

### 虚拟DOM
1. state
2. JSX 模板
3. 数据 + 模板 结合，生成真实DOM，来显示
4. state发生变化
5. 数据 + 模板 结合，生成真实DOM，替换原始的DOM
   
### 缺陷
1. 第一次生成了一个完整的DOM片段
2. 第二次生成了一个完整的DOM片段
3. 第二次的DOM替换第一次的DOM，非常消耗性能
   

### 优化 1
1. state
2. JSX 模板
3. 数据 + 模板 结合，生成真实DOM，来显示
4. state发生变化
5. 数据 + 模板 结合，生成真实DOM，并不替换原始DOM
6. 新的DOM（DocumentFragment）和旧的DOM做对比，找差异
7. 找出input框发生了变化
8. 只用新的DOM中的input元素，替换老的DOM中的input元素

### 缺陷
性能优化并不明显


### 优化2
1. state
2. JSX 模板
3. 生成虚拟DOM(虚拟DOM就是一个js对象，用它来描述真实的DOM)
4. 根据虚拟DOM生成真实DOM，来显示
6. state发生变化
7. 数据 + 模板 结合，生成新的虚拟DOM
8. 比较原始的虚拟DOM和新的虚拟DOM，找出区别
9. 直接操作DOM，修改span的内容
    
### 优点
1. 性能提升
2. 它使得跨端应用得以实现。React Native
