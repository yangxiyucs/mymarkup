# HTTP Basic Auth

[参考](https://blog.csdn.net/qq673318522/article/details/62047574)

[参考](https://blog.csdn.net/TinyJian/article/details/81067777)

在HTTP中，基本认证是一种用来允许Web浏览器或其他客户端程序在请求时提供**用户名**和**口令**形式的身份凭证的一种登录验证方式，通常用户名和明码会通过HTTP头传递。

在发送之前是以用户名追加一个冒号然后串接上口令，并将得出的结果字符串再用Base64算法编码。例如，提供的用户名是Aladdin、口令是open sesame，则拼接后的结果就是Aladdin:open sesame，然后再将其用`Base64编码`，得到QWxhZGRpbjpvcGVuIHNlc2FtZQ==。最终将Base64编码的字符串发送出去，由接收者解码得到一个由冒号分隔的用户名和口令的字符串。

- 优点

基本认证的一个优点是基本上所有流行的网页浏览器都支持基本认证。但是基本认证很少在可公开访问的互联网网站上使用，有时候会在小的私有系统中使用。 

- 缺点

由于用户名和密码都是Base64编码的，而Base64编码是可逆的，所以用户名和密码可以认为是明文。所以只有在客户端和服务器主机之间的连接是安全可信的前提下才可以使用。如果没有使用**SSL/TLS**这样的传输层安全的协议，那么以明文传输的密钥和口令很容易被拦截。 
由于现存的浏览器保存认证信息直到标签页或浏览器关闭，或者用户清除历史记录。导致了服务器端无法主动来当前用户登出或者认证失效。