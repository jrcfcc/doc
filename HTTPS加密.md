### HTTPS加密

#### 什么是HTTPS

https也就是http over ssl/tls 所有的http数据都是在ssl/tls 协议封装之上传输的。https协议在http协议的基础上,添加了ssl/tls握手和数据加密传输，ssl/tls也是应用层协议。所以研究https也就是研究ssl/tls。

#### TLS(Transport Layer Security)握手过程

目前最新的TLS协议版本是1.2,握手过程见下图

![TLS-handshake-protocol](C:\Users\jiang\Desktop\blog\images\TLS-handshake-protocol.png)

如上图所示，简易流程如下

-  客户端生成一个随机数Random-Client,传给服务端 
- 服务端生成一个随机数Random-Server,和公钥一起传给客户端 
- 客户端去CA机构验证证书的合法性,不合法则告警
- 客户端接收到的数据原封不动，加上Premaster Secret(通过Random-Client，Random-Server和一定的算法生成的),通过服务端传过来的公钥加密,传输给服务端
- 服务端使用私钥解密，得到Premaster Secret,此时双方都拿到了Random-Client，Random-Server和Premaster Secret的验证三要素
- 安全通道已建立,之后的数据传输都会校验通过Random-Client，Random-Server和Premaster Secret计算出来的session key(对称加密算出来的)

![640](C:\Users\jiang\Desktop\blog\images\640.webp)

