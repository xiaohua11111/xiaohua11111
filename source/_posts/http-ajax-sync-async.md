---
title: 关于HTTP请求、Ajax请求，请求的同步和异步
date: 2017-11-22 08:31:09
tags:
---
使用了很长时间的Ajax请求了，一直都是在以异步的方式在使用。昨天听了一个讲座涉及到apache server，偶然想到了这Ajax请求和HTTP请求的一些区别和联系，就在网上好好搜了一顿，把搜到的结果写一下，理清一下自己的头绪吧。    

首先最早是没有Ajax请求的，只有普通的HTTP请求，这个时候发送一次HTTP请求，Server端就会计算后将数据放在一个HTML网页上返回来，客户端需要刷新网页，也就是每次请求都刷新网页。Ajax请求实现了返回xml或者json数据而不是html，然后支持在html不变情况下动态更新页面内容而无需刷新。  

这是HTTP和Ajax的区别。  

以前我用Ajax只用了异步请求，就以为他俩的区别除了上述区别，还包括Ajax请求是异步的，HTTP是同步的，这种误解当然是错的。  

不管传统的HTTP请求还是Ajax请求，都有同步和异步两种选项。  

仍以Ajax请求为例，该请求最终通过JavaScript的XMLHttpRequest发送，这个请求对象实例化的时候第二个参数可以配置同步或异步，配置为同步之后会阻塞浏览器页面的线程（也可能是进程），返回结果前客户端不再响应用户请求。配置为异步之后不会阻塞浏览器线程，继续进行浏览器渲染和响应用户操作，直到response返回后回调函数处理结果。  

最后还要说一点现在普遍使用Ajax的情况下，传统Http请求主要用于资源文件的请求。  