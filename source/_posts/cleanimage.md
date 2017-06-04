---
layout: clear
title: 删除冗余图片
date: 2017-06-04 18:56:25
tags:
banner: /img/kill.jpg
---

2017-06-03 23:57:25

这两天和大芒果讨论了一下关于在项目中清除冗余图片的问题，之前没有关注到这块，整理一下在
这个方面搜集到的资料。

2017-06-04 10:48:01
清除冗余是一个有意思的问题，同理可以衍生出一些其他的可以操作的比如清除冗余的CSS。清除冗余
js方法等等。
另外这个问题的场景比较固定，只考虑在前端静态页面开发过程中引入的图片资源问题。如果扩散一下
删除冗余图片的问题可能会复杂些，例如：如何删除博客上传的冗余图片 [知乎上面的这个问题](https://www.zhihu.com/question/36277221?from=profile_question_card)

当然好像都有解决方案

1. [gulp-unused-images](https://www.npmjs.com/package/gulp-unused-images)
2. [gulp-delete-unused-images](https://www.npmjs.com/package/gulp-delete-unused-images)
3. 有位兄台用Python  写了个方法[文章](http://blog-lision.com/2017/03/09/CleanUnUseedImg/?utm_source=tuicool&utm_medium=referral)

2017-06-04 18:56:59

我们想了在webpack上面实现这个功能,当然也有人关注到这个方面
1. [unused-files-webpack-plugin](https://github.com/tomchentw/unused-files-webpack-plugin)