###rsa加密过程

参考文档
https://my.oschina.net/mywiki/blog/1613886

rsa 是利用质数的一些性质进行的加密
详细

整体如下

    (1)求 N	用伪随机数生成质数 p、q, N = p * q
    (2)求 L	L = lcm(p-1, q-1)，L是q-1,p-1的最小公倍数
    (3)求 E	1 < E < L, gcd(E, L)=1, E、L互质
    (4)求 D	1 < D < L, E * d mod L = 1
    
    参考https://blog.csdn.net/u010039377/article/details/79904467

####网易云使用的js的代码
    rsa in javascript
    http://www.ohdave.com/rsa/