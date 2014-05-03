---
layout: post
title: "cocoapods specs 镜像"
description: ""
category: ""
tags: [cocoapods,specs]
---
{% include JB/setup %}

在使用cocoapods 进行update 或者 install的时候 每次回去更新获取的pod specs，每次速度都不是很理想，博主最近对github上的specs仓库进行了镜像，分别在[gitcafe](https://gitcafe.com/akuandev/Specs.git) 和 [oschina](http://git.oschina.net/akuandev/Specs.git) 现在每10分钟会进行一次同步 基本和主仓库保持一致

使用方法：
	
	pod repo remove master
	pod repo add master https://gitcafe.com/akuandev/Specs.git
	pod repo update
	
如果想用oschina的镜像也可以把第二条命令 换成 `http://git.oschina.net/akuandev/Specs.git` 即可

第二条命令执行的时候会比较耗时 这个时候要去把整个specs仓库clone一下 大概60M左右

如果你还没有使用过coacoapods 这里有一份安装的介绍 [cocoapods 使用](http://akindev.tk/post/cocoapods-ios-library-manager)

如果不想在pod install pod update的时候不想升级specs库 可以使用参数忽略掉 

		pod install --verbose --no-repo-update
		pod update --verbose --no-repo-update
