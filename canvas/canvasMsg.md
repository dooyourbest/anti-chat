##canvas指纹
在对作弊的过程中，我们发现有其他的方式，进行防作弊
####1 canvas 指纹方案
##### 原理
#####不同的机器不同的硬件对于 Canvas 画出的图总是存在像素级别的误差，因此我们判断当对于访问来说大量的 canvas 的指纹一致的话，则认为是爬虫，则可以封掉它
    参考:
    https://www.cnblogs.com/leijing0607/p/8044218.html
    在一些情况下，作弊者会使用代理ip,购买手机短信等方式进行进行抓取信息，如果canvas指纹可以进行跟踪，
    对于同一指纹的用户，如果同时发送了大量的请求信息，而且ip不同，手机号码不同，
    我们可以认为是用的同一设备，可以进行有效的防作弊
##### 一个获取 canvas指纹的网站和canvas指纹介绍
https://browserleaks.com/canvas
##### how-does-it-work
https://browserleaks.com/canvas#how-does-it-work

