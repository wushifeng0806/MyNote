### IO模型

https://blog.csdn.net/ZWE7616175/article/details/80591587

### TCP协议

https://www.cnblogs.com/cenglinjinran/p/8482412.html

### TCP中的time_wait状态

https://www.cnblogs.com/cenglinjinran/p/8482412.html

### Tomcat类加载

https://www.cnblogs.com/aspirant/p/8991830.html



### 加密和签名的区别

加密是为了防泄露

签名是为了防伪造、防篡改

### 对称加密与非对称加密的区别

- 对称加密: 加密和解密的秘钥使用的是同一个.
- 非对称加密: 与对称加密算法不同，非对称加密算法需要两个密钥：公开密钥（publickey）和私有密钥（privatekey）。

### JWT（Json Web Token）

可以看这篇：

https://baijiahao.baidu.com/s?id=1608021814182894637

### JWT的缺点

1、JWT默认不加密，但可以加密。生成原始令牌后，可以使用改令牌再次对其进行加密。

2、当JWT未加密方法是，一些私密数据无法通过JWT传输。

3、JWT不仅可用于认证，还可用于信息交换。善用JWT有助于减少服务器请求数据库的次数。

4、JWT的最大缺点是服务器不保存会话状态，所以在使用期间不可能取消令牌或更改令牌的权限。也就是说，一旦JWT签发，在有效期内将会一直有效。

5、JWT本身包含认证信息，因此一旦信息泄露，任何人都可以获得令牌的所有权限。为了减少盗用，JWT的有效期不宜设置太长。对于某些重要操作，用户在使用时应该每次都进行进行身份验证。

6、为了减少盗用和窃取，JWT不建议使用HTTP协议来传输代码，而是使用加密的HTTPS协议进行传输。