---
layout: post
title: 记录一次gitbook转pdf的坑
categories: Git
description: gitbook
keywords: git node note
---
## Mac上将gitbook转化成pdf文档下载
 
 #### 安装gitbook-cli 以及 gitbook
 ```
 sudo npm install -g gitbook-cli
 sudo npm install -g gitbook
```
##### 到这里都没有问题

#### 安装完成后检查gitbook -V
``` 
CLI version: 2.3.2
GitBook version: 3.2.3
```
#### cd到gitbook项目的目录 执行
```
 gitbook pdf 
```
##### 报错

```
error: error while generating page "README.md": 

InstallRequiredError: "svgexport" is not installed.
Install it using: "npm install svgexport -g"
```

#### 既然错了 那就安装呗 
执行
```
sudo npm install svgexport -g
```
##### 卧槽 这是什么情况？？？安装怎么报错 

```
Removing /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt/lib/phantom
Copying extracted folder /tmp/phantomjs/phantomjs-2.1.1-macosx.zip-extract-1559046754509/phantomjs-2.1.1-macosx -> /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt/lib/phantom
chmod failed: phantomjs was not successfully copied to /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt/lib/phantom/bin/phantomjs
```
#### 卸载重装
```
sudo npm uninstall svgexport -g
sudo npm install svgexport -g
```
##### 特么还是一样的错误

#### 多试了几次 还是不行 那就问google爸爸吧

####  stackoverflow上有个方法 在后边执行加上  
```
sudo npm install svgexport -g  --ignore-scripts
```
#### 结果竟然成功了，圣母玛利亚。。此时距离我折腾这个已经过去了三个小时了

#### 激动人心的时刻到了 

```
gitbook pdf
```
#### 结果呢？！！！！卧槽 卧槽！！！！ 
```
error: error while generating page "README.md": 

Error: Error with command "svgexport"
```

#### 又是这个问题？？？ 
#### 我这时候看了看上边的错误，发现了 chmod failed 这个提示，这个应该是权限的问题吧？？文件夹拷贝的时候没有权限造成的吧，。。。
#### 怎么办？？

#### 机智如我，想到了一个办法 cd 到这个目录下

 ``` 
 cd  /usr/local/lib/node_modules/svgexport

 sudo rm -rf  node_modules
 ```

 #### 直接全删了 ，然后重新安装
 ```
sudo npm i
 ```

 ```
phantomjs-prebuilt@2.1.16 install /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt
> node install.js

Considering PhantomJS found at /usr/local/bin/phantomjs
Looks like an `npm install -g`
Could not link global install, skipping...
Download already available at /tmp/phantomjs/phantomjs-2.1.1-macosx.zip
Verified checksum of previously downloaded file
Extracting zip contents
Removing /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt/lib/phantom
Copying extracted folder /tmp/phantomjs/phantomjs-2.1.1-macosx.zip-extract-1559047678773/phantomjs-2.1.1-macosx -> /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt/lib/phantom
Writing location.js file
Done. Phantomjs binary available at /usr/local/lib/node_modules/svgexport/node_modules/phantomjs-prebuilt/lib/phantom/bin/phantomjs
npm notice created a lockfile as package-lock.json. You should commit this file.
added 192 packages from 571 contributors and audited 328 packages in 6.57s
found 0 vulnerabilities
 ```

 #### 安装成功

 #### 然后再执行 gitbook pdf

#### 搞定！！！！！ 文件夹里 book.pdf在文件夹里躺着呢！！！！









 