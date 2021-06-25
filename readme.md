

# Linux

可以掌握常用工具的日常使用场景：

- [ ] awk统计ip

  - [x] awk基本内置变量：FS、OFS、RS、ORS、NR、NF（输出最后一个字段，`$NF`）、BEGIN、END、FILENAME、ARGC、ARGV

  - [x] printf：格式化输出

  - [x] print：正常输出

  - [x] 模式匹配：匹配字符使用`/[string]/`括起来

    - [x] 匹配所有行中只要含`root`的行：`awk '/root/ {print $0} 1.txt'`
    - [x] `^`符号表示开头，比如：`awk '/^root/ {print $0} 1.txt'`，该语句输出`1.txt`文件中的所有以`root`开头的行

  - [x] 运算符匹配：

    > `>`、`<`、`>=`、`<=`、`==`、`!=`、`~`（匹配正则表达式）、`!~`（不匹配正则表达式）
    >
    > - [x] 如果需要对某个变量进行匹配，则需要在变量后面加上`~`符号，表示匹配的意思，比如：`awk '$1~/root/ {print $0} 1.txt'`

  - [x] 布尔运算符：

    > `&&`，与符号用于连接多个匹配关系：`$3>50 && $3<100`，即第三个变量大于50且小于100
    >
    > `||`，或符号
    >
    > `!`，非符号

    计算文件中的所有空白行的总数

- [ ] grep

- [ ] find

- [x] curl

  > curl means client URL tool, curl in short.
  >
  > [curl tutorials in chinese](http://www.ruanyifeng.com/blog/2019/09/curl-reference.html)
  >
  > - **get** request: 
  >
  >   ```bash
  >   curl https://www.baidu.com   # default request is get
  >   ```
  >
  > - `-A`: user can specfiy the user-agent of th request
  >
  > - `-b`: send a cookie to server
  >
  >   ```bash
  >   curl -b 'foo=bar;foo2=bar2;...' https://www.baidu.com  # cookie name is foo, value is bar
  >   curl -b cookie.txt https://www.baidu.com  # send the cookie file to server 
  >   ```
  >
  > - `-c`: write the cookie information that server sent to client into a file
  >
  > - `-d`: If you want to use **POST** request to access website, you should send data to server.
  >
  >   ```bash
  >   curl -d 'username=admin&passwd=admin' [X POST] https://www.baidu.com
  >   curl -d '@data.txt' https://www.baidu.com  # post data is in a file
  >   ```
  >
  > - `--data-urlencode`: same as `-d`, this command can change the data to urlcode.

- [x] 了解：logrotate，rsync

  - [x] logrotate

    > [logrotate](https://linux.die.net/man/8/logrotate) - rotates, compresses, and mails system logs
    >
    > [logrotate tutorials in chinese](https://www.jianshu.com/p/81dd446a1cb1)

  - [x] rsync

    > [rsync](https://linux.die.net/man/1/rsync) -- a fast, versatile, remote (and local) file-copying tool
    >
    > The `rsync` can replace the command `cp` in linux, for example, you can use `rsync -r source destination` to replace `cp -r source destination `.
    >
    > [video tutorials](https://www.bilibili.com/video/BV1qZ4y137En?from=search&seid=10542537430323288651)
    >
    > sync local file:
    >
    > ```bash
    > $ rsync -a source destination
    > ```
    >
    > sync remote host file:
    >
    > ```bash
    > $ rsync -av -e 'ssh -p 22' [source] user@remoteHostAddress:[destination] 
    > ```
    >
    > `-v`   display the details of the information
    >
    > `-a`   archive mode
    >
    > `-e`   log in to remote host

- [ ] 掌握ansible基本用法：主要用于批量查日志，执行命令。

  > [Ansible中文权威指南](https://ansible-tran.readthedocs.io/en/latest/index.html)

# Http：

- [x] 常用header: Host

  - [x] 请求：request

    | Header              | 解释                                                         | 示例                                                         |
    | :------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
    | Accept              | 指定客户端能够接收的内容类型                                 | Accept: text/plain, text/html                                |
    | Accept-Charset      | 浏览器可以接受的字符编码集。                                 | Accept-Charset: iso-8859-5                                   |
    | Accept-Encoding     | 指定浏览器可以支持的web服务器返回内容压缩编码类型。          | Accept-Encoding: compress, gzip                              |
    | Accept-Language     | 浏览器可接受的语言                                           | Accept-Language: en,zh                                       |
    | Accept-Ranges       | 可以请求网页实体的一个或者多个子范围字段                     | Accept-Ranges: bytes                                         |
    | Authorization       | HTTP授权的授权证书                                           | Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==            |
    | Cache-Control       | 指定请求和响应遵循的缓存机制                                 | Cache-Control: no-cache                                      |
    | Connection          | 表示是否需要持久连接。（HTTP 1.1默认进行持久连接）           | Connection: close                                            |
    | Cookie              | HTTP请求发送时，会把保存在该请求域名下的所有cookie值一起发送给web服务器。 | Cookie: $Version=1; Skin=new;                                |
    | Content-Length      | 请求的内容长度                                               | Content-Length: 348                                          |
    | Content-Type        | 请求的与实体(body)对应的MIME信息                             | Content-Type: application/x-www-form-urlencoded              |
    | Date                | 请求发送的日期和时间                                         | Date: Tue, 15 Nov 2010 08:12:31 GMT                          |
    | Expect              | 请求的特定的服务器行 为                                      | Expect: 100-continue                                         |
    | From                | 发出请求的用户的Email                                        | From: [user@email.com](mailto:user@email.com)                |
    | **Host**            | **指定请求的服务器的域名和端口号**                           | **Host: [www.baidu.com](https://www.baidu.com/)**            |
    | If-Match            | 只有请求内容与实体相匹配才有效                               | If-Match: “737060cd8c284d8af7ad3082f209582d”                 |
    | If-Modified-Since   | 如果请求的部分在指定时间之后被修改则请求成功，未被修改则返回304代码 | If-Modified-Since: Sat, 29 Oct 2010 19:43:31 GMT             |
    | If-None-Match       | 如果内容未改变返回304代码，参数为服务器先前发送的Etag，与服务器回应的Etag比较判断是否改变 | If-None-Match: “737060cd8c284d8af7ad3082f209582d”            |
    | If-Range            | 如果实体未改变，服务器发送客户端丢失的部分，否则发送整个实体。参数也为Etag | If-Range: “737060cd8c284d8af7ad3082f209582d”                 |
    | If-Unmodified-Since | 只在实体在指定时间之后未被修改才请求成功                     | If-Unmodified-Since: Sat, 29 Oct 2010 19:43:31 GMT           |
    | Max-Forwards        | 限制信息通过代理和网关传送的时间                             | Max-Forwards: 10                                             |
    | Pragma              | 用来包含实现特定的指令                                       | Pragma: no-cache                                             |
    | Proxy-Authorization | 连接到代理的授权证书                                         | Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==      |
    | Range               | 只请求实体的一部分，指定范围                                 | Range: bytes=500-999                                         |
    | Referer             | 先前网页的地址，当前请求网页紧随其后,即来路                  | Referer: [http://www.baidu.com/archives/71.html](https://www.baidu.com/archives/71.html) |
    | TE                  | 客户端愿意接受的传输编码，并通知服务器接受接受尾加头信息     | TE: trailers,deflate;q=0.5                                   |
    | Upgrade             | 向服务器指定某种传输协议以便服务器进行转换（如果支持）       | Upgrade: HTTP/2.0, SHTTP/1.3, IRC/6.9, RTA/x11               |
    | User-Agent          | User-Agent的内容包含发出请求的用户信息                       | User-Agent: Mozilla/5.0 (Linux; X11)                         |
    | Via                 | 通知中间网关或代理服务器地址，通信协议                       | Via: 1.0 fred, 1.1 nowhere.com (Apache/1.1)                  |
    | Warning             | 关于消息实体的警告信息                                       | Warn: 199 Miscellaneous warning                              |

  - [x] 相应：response

    | Header             | 解释                                                         | 示例                                                         |
    | :----------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
    | Accept-Ranges      | 表明服务器是否支持指定范围请求及哪种类型的分段请求           | Accept-Ranges: bytes                                         |
    | Age                | 从原始服务器到代理缓存形成的估算时间（以秒计，非负）         | Age: 12                                                      |
    | Allow              | 对某网络资源的有效的请求行为，不允许则返回405                | Allow: GET, HEAD                                             |
    | Cache-Control      | 告诉所有的缓存机制是否可以缓存及哪种类型                     | Cache-Control: no-cache                                      |
    | Content-Encoding   | web服务器支持的返回内容压缩编码类型。                        | Content-Encoding: gzip                                       |
    | Content-Language   | 响应体的语言                                                 | Content-Language: en,zh                                      |
    | Content-Length     | 响应体的长度                                                 | Content-Length: 348                                          |
    | Content-Location   | 请求资源可替代的备用的另一地址                               | Content-Location: /index.htm                                 |
    | Content-MD5        | 返回资源的MD5校验值                                          | Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==                        |
    | Content-Range      | 在整个返回体中本部分的字节位置                               | Content-Range: bytes 21010-47021/47022                       |
    | Content-Type       | 返回内容的MIME类型                                           | Content-Type: text/html; charset=utf-8                       |
    | Date               | 原始服务器消息发出的时间                                     | Date: Tue, 15 Nov 2010 08:12:31 GMT                          |
    | ETag               | 请求变量的实体标签的当前值                                   | ETag: “737060cd8c284d8af7ad3082f209582d”                     |
    | Expires            | 响应过期的日期和时间                                         | Expires: Thu, 01 Dec 2010 16:00:00 GMT                       |
    | Last-Modified      | 请求资源的最后修改时间                                       | Last-Modified: Tue, 15 Nov 2010 12:45:26 GMT                 |
    | Location           | 用来重定向接收方到非请求URL的位置来完成请求或标识新的资源    | Location: [http://honglu.me/archives/](https://honglu.me/archives/) |
    | Pragma             | 包括实现特定的指令，它可应用到响应链上的任何接收方           | Pragma: no-cache                                             |
    | Proxy-Authenticate | 它指出认证方案和可应用到代理的该URL上的参数                  | Proxy-Authenticate: Basic                                    |
    | refresh            | 应用于重定向或一个新的资源被创造，在5秒之后重定向（由网景提出，被大部分浏览器支持） | Refresh: 5; url=[http://honglu.me/archives/](https://honglu.me/archives/) |
    | Retry-After        | 如果实体暂时不可取，通知客户端在指定时间之后再次尝试         | Retry-After: 120                                             |
    | Server             | web服务器软件名称                                            | Server: Apache/1.3.27 (Unix) (Red-Hat/Linux)                 |
    | Set-Cookie         | 设置Http Cookie                                              | Set-Cookie: UserID=JohnDoe; Max-Age=3600; Version=1          |
    | Trailer            | 指出头域在分块传输编码的尾部存在                             | Trailer: Max-Forwards                                        |
    | Transfer-Encoding  | 文件传输编码                                                 | Transfer-Encoding:chunked                                    |
    | Vary               | 告诉下游代理是使用缓存响应还是从原始服务器请求               | Vary: *                                                      |
    | Via                | 告知代理客户端响应是通过哪里发送的                           | Via: 1.0 fred, 1.1 nowhere.com (Apache/1.1)                  |
    | Warning            | 警告实体可能存在的问题                                       | Warning: 199 Miscellaneous warning                           |
    | WWW-Authenticate   | 表明客户端请求实体应该使用的授权方案                         | WWW-Authenticate: Basic                                      |

- [x] 跨域 Cookie

  > [COOKIE跨域获取问题](https://segmentfault.com/a/1190000039227924)
  >
  > [video tutorials in chinese](https://www.bilibili.com/video/BV1pA411u7Ji?from=search&seid=5785122887893488786)
  >
  > [ What does CORS means](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CORS)
  >
  > [CORS tutorials: A guide to cross-origin resource sharing](https://auth0.com/blog/cors-tutorial-a-guide-to-cross-origin-resource-sharing/)
  >
  > 网址形式如下：https://www.baidu.com:80/index.html，其中，`https`是协议，`www`是子域名，`baidu.com`是根域名，`80`是端口号，`index.html`是资源文件。
  >
  > > **同源策略**是指在[Web浏览器](https://zh.wikipedia.org/wiki/排版引擎)中，允许某个网页[脚本](https://zh.wikipedia.org/wiki/腳本)访问另一个网页的数据，但前提是这两个网页必须有相同的[URI](https://zh.wikipedia.org/wiki/统一资源标志符)、[主机名](https://zh.wikipedia.org/wiki/主機名稱)和[端口号](https://zh.wikipedia.org/wiki/通訊埠)，一旦两个网站满足上述条件，这两个网站就被认定为具有相同来源。此策略可防止某个网页上的恶意[脚本](https://zh.wikipedia.org/wiki/脚本)通过该页面的[文档对象模型](https://zh.wikipedia.org/wiki/文档对象模型)访问另一网页上的敏感数据。
  > >
  > > 同源策略对[Web应用程序](https://zh.wikipedia.org/wiki/Web应用程序)具有特殊意义，因为Web应用程序广泛依赖于[HTTP cookie](https://zh.wikipedia.org/wiki/Cookie)[[1\]](https://zh.wikipedia.org/wiki/同源策略#cite_note-httpcookierfc-1)来维持用户[会话](https://zh.wikipedia.org/wiki/会话)，所以必须将不相关网站严格分隔，以防止丢失数据泄露。
  > >
  > > 值得注意的是同源策略仅适用于脚本，这意味着某网站可以通过相应的[HTML标签](https://zh.wikipedia.org/wiki/HTML标签)[[2\]](https://zh.wikipedia.org/wiki/同源策略#cite_note-2)访问不同来源网站上的[图像](https://zh.wikipedia.org/wiki/图像)、[CSS](https://zh.wikipedia.org/wiki/CSS)和[动态加载](https://zh.wikipedia.org/wiki/動態加載)[脚本](https://zh.wikipedia.org/wiki/脚本)等资源。而[跨站请求伪造](https://zh.wikipedia.org/wiki/跨站请求伪造)就是利用同源策略不适用于[HTML标签](https://zh.wikipedia.org/wiki/HTML标签)的缺陷。
  >
  > 在`协议`、`域名（包括根域名和子域名）`、`端口号`三者其中任何一项不一致的情况下，两个网址就不能进行互相通信，只有这三者都相同的情况下才可以进行通信，否则就叫**跨域**。
  >
  > - a different scheme(http or https)
  > - a different domain
  > - a different port
  >
  > > **为什么会有跨域限制？**
  > >
  > > 答：浏览器会有跨域限制，二服务器没有这种限制。
  >
  > 在HTML标签中，其中`img`、`link`、`script`、`iframe`这几个标签具有跨域性，可以直接访问不同域的资源。
  >
  > **figure it out**
  >
  > - set the header like this: 
  >
  >   ```bash
  >   Access-Control-Allow-Origin: *  # if a request can be made from any origin
  >   Access-Control-Allow-Origin: https://example.com # the origin that is allowed to make the request
  >   ```
  >
  > **Two type of CORS Request**
  >
  > - simple request(`GET`、`POST`、`HEAD`)
  >
  > - preflight request(`OPTIONS`)
  >
  >   A preflight request example:
  >
  >   ```bash
  >   # Request
  >   curl -i -X OPTIONS localhost:3001/api/ping \
  >   -H 'Access-Control-Request-Method: GET' \
  >   -H 'Access-Control-Request-Headers: Content-Type, Accept' \
  >   -H 'Origin: http://localhost:3000'
  >   ```
  >
  >   

- [x] https原理

  HTTP协议是一种不安全的传输协议，所有数据在传输过程都是明文传输，很容易被第三方截获，造成数据不安全。

  HTTPS使用混合加密协议对数据进行加密，即对称加密和非对称加密：

  对称加密和非对称加密的优缺点：

  - 对称加密的加密和解密的速度快，效率高；非对称加密算法的加密和解密的速度满，效率低
  - 对称加密算法的加密和解密都是用的同一个密钥，密钥的传输成本较高；非对称加密算法的加密和解密采用的是不同的密钥，一个公钥一个私钥，公钥可以对外公开，密钥传输的成本较低。

  ![https://segmentfault.com/img/bVbClUj](https://segmentfault.com/img/bVbClUj)

  > **Hypertext Transfer Protocol Secure** (**HTTPS**) is an extension of the [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) (HTTP). It is used for [secure communication](https://en.wikipedia.org/wiki/Secure_communications) over a [computer network](https://en.wikipedia.org/wiki/Network_operating_system), and is widely used on the Internet.[[1\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-1)[[2\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-2) In HTTPS, the [communication protocol](https://en.wikipedia.org/wiki/Communication_protocol) is encrypted using [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) or, formerly, Secure Sockets Layer (SSL). The protocol is therefore also referred to as **HTTP over TLS**,[[3\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-3) or **HTTP over SSL**.
  >
  > The principal motivations for HTTPS are [authentication](https://en.wikipedia.org/wiki/Authentication) of the accessed [website](https://en.wikipedia.org/wiki/Website), and protection of the [privacy](https://en.wikipedia.org/wiki/Information_privacy) and [integrity](https://en.wikipedia.org/wiki/Data_integrity) of the exchanged data while in transit. It protects against [man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attack), and the bidirectional [encryption](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation) of communications between a client and server protects the communications against [eavesdropping](https://en.wikipedia.org/wiki/Eavesdropping) and [tampering](https://en.wikipedia.org/wiki/Tamper-evident#Tampering).[[4\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-httpse-4)[[5\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-5) The authentication aspect of HTTPS requires a trusted third party to sign server-side [digital certificates](https://en.wikipedia.org/wiki/Public_key_certificate). This was historically an expensive operation, which meant fully authenticated HTTPS connections were usually found only on secured payment transaction services and other secured corporate information systems on the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web). In 2016, a campaign by the [Electronic Frontier Foundation](https://en.wikipedia.org/wiki/Electronic_Frontier_Foundation) with the support of web browser developers led to the protocol becoming more prevalent.[[6\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-6) HTTPS is now used more often by web users than the original non-secure HTTP, primarily to protect page authenticity on all types of websites; secure accounts; and to keep user communications, identity, and web browsing private.[[7\]](https://en.wikipedia.org/wiki/HTTPS#cite_note-7)

  `HTTPS=HTTP+TLS/SSL`

  ![](https://segmentfault.com/img/bVbClUl)

  数字正式在HTTPS中相当于非对称加密算法的私钥和公钥的分配这么一个工作。

  > [HTTPS 详解一：附带最精美详尽的 HTTPS 原理图](https://segmentfault.com/a/1190000021494676)

# Redis

- [ ] hash,zset,set,string 等数据类型的常用指令和时间复杂度

  > - [x] **string**: 
  >
  > add a key-value type data, use `set key value` command
  >
  > ```bash
  > > set name zhangsan
  > OK
  > ```
  >
  >  read the value of the key given by user
  >
  > ```bash
  > > get name
  > "zhangsan"
  > ```
  >
  > | 序号 | 命令及描述                                                   | means                             |
  > | :--- | ------------------------------------------------------------ | --------------------------------- |
  > | 1    | [SET key value](https://www.runoob.com/redis/strings-set.html) 设置指定 key 的值 | **add a new key-value type data** |
  > | 2    | [GET key](https://www.runoob.com/redis/strings-get.html) 获取指定 key 的值。 | **read key;s value**              |
  > | 3    | [GETRANGE key start end](https://www.runoob.com/redis/strings-getrange.html) 返回 key 中字符串值的子字符 | **read the substring of the key** |
  > | 4    | [GETSET key value](https://www.runoob.com/redis/strings-getset.html) 将给定 key 的值设为 value ，并返回 key 的旧值(old value)。 | **change key's value**            |
  > | 5    | [GETBIT key offset](https://www.runoob.com/redis/strings-getbit.html) 对 key 所储存的字符串值，获取指定偏移量上的位(bit)。 |                                   |
  > | 6    | [MGET key1 [key2..\]](https://www.runoob.com/redis/strings-mget.html) 获取所有(一个或多个)给定 key 的值。 |                                   |
  > | 7    | [SETBIT key offset value](https://www.runoob.com/redis/strings-setbit.html) 对 key 所储存的字符串值，设置或清除指定偏移量上的位(bit)。 |                                   |
  > | 8    | [SETEX key seconds value](https://www.runoob.com/redis/strings-setex.html) 将值 value 关联到 key ，并将 key 的过期时间设为 seconds (以秒为单位)。 |                                   |
  > | 9    | [SETNX key value](https://www.runoob.com/redis/strings-setnx.html) 只有在 key 不存在时设置 key 的值。 |                                   |
  > | 10   | [SETRANGE key offset value](https://www.runoob.com/redis/strings-setrange.html) 用 value 参数覆写给定 key 所储存的字符串值，从偏移量 offset 开始。 |                                   |
  > | 11   | [STRLEN key](https://www.runoob.com/redis/strings-strlen.html) 返回 key 所储存的字符串值的长度。 |                                   |
  > | 12   | [MSET key value [key value ...\]](https://www.runoob.com/redis/strings-mset.html) 同时设置一个或多个 key-value 对。 |                                   |
  > | 13   | [MSETNX key value [key value ...\]](https://www.runoob.com/redis/strings-msetnx.html) 同时设置一个或多个 key-value 对，当且仅当所有给定 key 都不存在。 |                                   |
  > | 14   | [PSETEX key milliseconds value](https://www.runoob.com/redis/strings-psetex.html) 这个命令和 SETEX 命令相似，但它以毫秒为单位设置 key 的生存时间，而不是像 SETEX 命令那样，以秒为单位。 |                                   |
  > | 15   | [INCR key](https://www.runoob.com/redis/strings-incr.html) 将 key 中储存的数字值增一。 |                                   |
  > | 16   | [INCRBY key increment](https://www.runoob.com/redis/strings-incrby.html) 将 key 所储存的值加上给定的增量值（increment） 。 |                                   |
  > | 17   | [INCRBYFLOAT key increment](https://www.runoob.com/redis/strings-incrbyfloat.html) 将 key 所储存的值加上给定的浮点增量值（increment） 。 |                                   |
  > | 18   | [DECR key](https://www.runoob.com/redis/strings-decr.html) 将 key 中储存的数字值减一。 |                                   |
  > | 19   | [DECRBY key decrement](https://www.runoob.com/redis/strings-decrby.html) key 所储存的值减去给定的减量值（decrement） 。 |                                   |
  > | 20   | [APPEND key value](https://www.runoob.com/redis/strings-append.html) 如果 key 已经存在并且是一个字符串， APPEND 命令将指定的 value 追加到该 key 原来值（value）的末尾。 |                                   |

- [ ] 掌握正确的redis分布式锁。

# mysql

- [ ] 了解索引结构

- [ ] 常用索引优化技巧

# 其他：

- [x] markdown语法和 typora 使用

- [ ] git command

  - [x] add files to the remote repository

    > 4 steps when you `git` files to the remote repository:
    >
    > 1. git add filename1, filename2, ....  or git add * (add all)
    > 2. git commit -m "add a hit here"
    > 3. git remote add origin "repository address"
    > 4. git push origin branch_name (such as: master)

  - [x] merge 

    > ```bash
    > $ git merge <branch name>  # when you are in a branch, this command means merge <branch name> to this branch 
    > 
    > Jums@Computer MINGW64 ~/OneDrive/learngit (master) # current branch is master, merge <topic> to master
    > $ git merge topic
    > Auto-merging readme.md
    > CONFLICT (content): Merge conflict in readme.md
    > Auto-merging 2.py
    > CONFLICT (content): Merge conflict in 2.py
    > Removing 1.py
    > Automatic merge failed; fix conflicts and then commit the result.
    > ```
    >
    > **How to fix merge conflict:**
    >
    > When the merge conflict comes: When two files have two different sets of modifications in the same location, git cannot decide which modification to use and needs to be manually specified.
    >
    > The codes bewteen `<<<<<<<HEAD` and `=======` is in the current branch, and the codes bewtten `=======` and `>>>>>>[branch name]` is in the [branch name]. You shoud manually merged the codes.
    >
    > After that, you also should `add` the files to repository, use the following command:
    >
    > ```bash
    > $ git add [file name]
    > $ git commit -m ""  # you can't add the [file name] here, or you will get a error
    > ```

  - [x] rebase

    > [git-rebase](https://git-scm.com/docs/git-rebase) - Reapply commits on top of another base tip
    >
    > https://www.bilibili.com/video/BV19B4y1u7vm?from=search&seid=7525997366811669539    (video tutroials)

  - [x] reset 

    > 对提交的版本进行回退，可以根据`git  log`命令查看已经提交的版本，然后可以根据指定`commit id`或者`HEAD`回退到不同的版本，
    >
    > `git log`信息如下：
    >
    > ```bash
    > $ git log
    > commit 466755c74ed4fd27059f6b0e4f42d0c3dcb8b663 (HEAD -> master, origin/master)
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Mon Jun 21 14:58:11 2021 +0800
    > 
    > add a second title
    > 
    > commit b57119f13a741f116daabfebd27b51a990b7322a
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Mon Jun 21 14:39:35 2021 +0800
    > 
    > modified the file, add a new line
    > 
    > commit 1f7990b84caf752f9e22d1dbcf215d5285066d25
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Mon Jun 21 14:27:27 2021 +0800
    > 
    > first time to commit
    > ```
    >
    > `HEAD`表示当前的版本号，如果需要回退到上一个版本号，则可以使用`HEAD^`、上上一个版本号则是`HEAD^^`、往上倒100个可以在`HEAD`后面写上100个`^`符号，当然也可以写成`HEAD~100`。
    >
    > `HEAD`在`git`中其实是一个指针，指向不同的版本号，回退也就是将`HEAD`指针重新指向了不同的版本信息。
    >
    > ![](https://jums.club/images/article/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20210621152126.png)
    >
    > 除了使用`HEAD`之外，还可以使用`commit id`进行回退，每一次版本提交都有一个宇宙唯一的`commit id`，指定该`commit id`的前几位就行，`git`会自行查找。
    >
    > ```bash
    > $ git reset --hard HEAD~2
    > HEAD is now at 1f7990b first time to commit
    > 
    > $ git reset --hard 466755
    > HEAD is now at 466755c add a second title
    > ```
    >
    > 在使用`git log`命令时，只会显示当前命令窗口的历史提交记录，如果电脑重启之后，在使用`git log`命令出现的历史记录会是空，但是在`git`中，就算是重启电脑之后，还是有办法找到每一次的历史提交记录，可以使用命令：`git reflog`：
    >
    > ```bash
    > $ git reflog
    > 1f7990b (HEAD -> master) HEAD@{0}: reset: moving to HEAD~2
    > 466755c (origin/master) HEAD@{1}: reset: moving to 466755
    > 1f7990b (HEAD -> master) HEAD@{2}: reset: moving to HEAD~2
    > 466755c (origin/master) HEAD@{3}: reset: moving to 466755
    > b57119f HEAD@{4}: reset: moving to HEAD^
    > 466755c (origin/master) HEAD@{5}: commit: add a second title
    > b57119f HEAD@{6}: commit: modified the file, add a new line
    > 1f7990b (HEAD -> master) HEAD@{7}: commit (initial): first time to commit
    > ```
    >
    > 在使用`reset`等命令修改了本地文件之后，也就是当前本地电脑上的文件不是`git`托管平台的最新版本的时候，需要使用`git pull`命令将`git`平台的命令拉过来。
    >
    > ```bash
    > git pull <remote_repository> <branch>
    > ```
    >
    > ```bash
    > $ git pull git@github.com:crazyjums/learngit.git master
    > From github.com:crazyjums/learngit
    >  * branch            master     -> FETCH_HEAD
    > Auto-merging readme.md
    > CONFLICT (content): Merge conflict in readme.md
    > Automatic merge failed; fix conflicts and then commit the result.
    > ```

  - [x] revert 

    > [git-revert](https://git-scm.com/docs/git-revert) - Revert some existing commits
    >
    > sounds like the `git reset` command, but this command can remain the trackability information, when you wana go back to the history version in `master` branch, you should use `git revert` command instead of `git reset`.
    >
    > This command's usage just like the `git reset`.
    >
    > ```bash
    > $ git revert HEAD^  # go back to last version
    > $ git revert HEAD~[number]  # go back to previous version
    > # you can see the trackability information at `git revert`:
    > commit d567e6e3e14165ffa8febd4c62bac2fa413a1509
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Thu Jun 24 11:33:43 2021 +0800
    > 
    >  Revert "add a txt file by jums"
    > 
    >  This reverts commit db298e7bb373711438efdab0e64bbab72b5b5cac.
    > ```

  - [x] checkout 

    > git-checkout - Switch branches or restore working tree files
    >
    > ```bash
    > $ git checkout <branch name>  # swtich to a new branch
    > ```
    >
    > ```bash
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (master)
    > $ git checkout new_branch
    > Switched to branch 'new_branch'
    > 
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (new_branch)
    > ```

  - [ ] stash 

    > [git-stash](https://git-scm.com/docs/git-stash) - Stash the changes in a dirty working directory away
    >
    > 应用场景：https://www.cnblogs.com/tocy/p/git-stash-reference.html
    >
    > - 发现有一个类是多余的，想删掉它又担心以后需要查看它的代码，想保存它但又不想增加一个脏的提交。这时就可以考虑`git stash`。
    > - 使用git的时候，我们往往使用分支（branch）解决任务切换问题，例如，我们往往会建一个自己的分支去修改和调试代码, 如果别人或者自己发现原有的分支上有个不得不修改的bug，我们往往会把完成一半的代码`commit`提交到本地仓库，然后切换分支去修改bug，改好之后再切换回来。这样的话往往log上会有大量不必要的记录。其实如果我们不想提交完成一半或者不完善的代码，但是却不得不去修改一个紧急Bug，那么使用`git stash`就可以将你当前未提交到本地（和服务器）的代码推入到Git的栈中，这时候你的工作区间和上一次提交的内容是完全一样的，所以你可以放心的修Bug，等到修完Bug，提交到服务器上后，再使用`git stash apply`将以前一半的工作应用回来。
    > - 经常有这样的事情发生，当你正在进行项目中某一部分的工作，里面的东西处于一个比较杂乱的状态，而你想转到其他分支上进行一些工作。问题是，你不想提交进行了一半的工作，否则以后你无法回到这个工作点。解决这个问题的办法就是`git stash`命令。储藏(stash)可以获取你工作目录的中间状态——也就是你修改过的被追踪的文件和暂存的变更——并将它保存到一个未完结变更的堆栈中，随时可以重新应用。
    >
    > ```bash
    > $ git stash list  # display all stash version
    > $ git stash pop   # get the top of the stash stack version
    > $ git stask apply [version number]# when there is a lot of stash versions, you can use this command to specify the version number
    > $ git stash   # save current working area to the stash version
    > $ git stash save [a stash name]  # the same as the "git stash", but this version will get a nick name you named it.
    > $ git stash drop  # delete the top of stash stack's version
    > $ git stash show [version number]   # use this command to view specific information of the working area
    > ```

  - [x] cherry-pick

    > [git-cherry-pick](https://git-scm.com/docs/git-cherry-pick) - Apply the changes introduced by some existing commits
    >
    > 应用场景：在多分支的分布式开发过程中，在合并代码时分两种情况，一种是将另一个分支中的所有代码都合并带当前分支中来，此时可以使用`git merge <branch name>`命令实现；还有一种情况是只需要将另一个分支中的部分代码合并到当前分支中来，这个时候就需要使用`git cherry-pick <commitHash>`命令来实现了，即将另一个分支的部分`commit`提交到当前的分支中。
    >
    > [Git进阶教程-5-5-如何再次应用已经存在的提交的修改](https://www.bilibili.com/video/BV1LK411F7mm?from=search&seid=8010070644096016508)   (videos tutorials)
    >
    > [git cherry-pick tutorials](http://www.ruanyifeng.com/blog/2020/04/git-cherry-pick.html)  (more commands informations here)
    >
    > ```bash
    > # at master branch
    > $ git add 1.txt && git commit -m "add a txt file"
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (master)
    > $ git log
    > commit db298e7bb373711438efdab0e64bbab72b5b5cac (HEAD -> master)
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Thu Jun 24 10:28:47 2021 +0800
    > 
    >  add a txt file
    > $ git checkout topic
    > $ git cherry-pick db298e7
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (topic)
    > $ git log
    > commit ed9bd8a0e76044141efdf26547092eae24e38400 (HEAD -> topic)
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Thu Jun 24 10:28:47 2021 +0800
    > 
    >  add a txt file
    > ```
    >
    > **if use the options [-n], it's no commits in current branch.**
    >
    > ```bash
    > $ git cherry-pick [-n]/[--no-commit] [commit-id]
    > ```
    >
    > **if use the options [-x], you can track the commits**
    >
    > ```bash
    > $ git cherry-pick -x [commit-id]
    > ASUS@ZHG_ASUS MINGW64 ~/OneDrive/learngit (topic)
    > $ git log
    > commit 6ba043389d5940b743ab39e37419ebc82685b0af (HEAD -> topic)
    > Author: crazyjums <crazyjums@gmail.com>
    > Date:   Thu Jun 24 10:41:48 2021 +0800
    > 
    >  add 2.txt
    > 
    >  (cherry picked from commit 771858e928c708923e843ffe4c29843f2900125a)  # this line will display the trackability information
    > ```
    >
    > **if use the options [-e] or [--edit], you can edit the file before you commit**
    >
    > ```bash
    > $ git cherry-pick -e [commit-id] # now it will jump to editing interface
    > ```

  - [x] branch

    > branche是git tree中的分支，其中主分支是master
    >
    > ```bash
    > $ git branch <branch name> # create a new branch 
    > $ git push origin <branch name> # push the new branch to remote repository
    > $ git branch -d <branch name> # delete the local branch
    > $ git push origin :<branch name> # delete the remote repository branch
    > $ git chechout <branch name> # swtich to <branch name> branch
    > $ git branch -a # show all branch of your repository
    > ```

  - [x] delete file from remote repository

    > ```bash
    > $ git rm <file name> or <dic name>
    > $ git commit -m ""
    > $ git push origin <branch name>
    > ```

- [x] ssh 秘钥登陆原理

  在远程连接Linux系统时，通常会采用SSH协议作为底层的安全协议，连接的格式如下：`ssh user@hostAddr`

  加密方式同样采用的混合加密技术，即对称加密和非对称加密的混合使用

  - [x] [SSH 协议基本原理及 wireshark 抓包分析](https://juejin.cn/post/6844903685047189512)

  远程主机和当前主机如何保证公钥的一致性，即如果防止中间人攻击：主机将自身的公钥公示于网络，即大众可查询的媒体上面，如果需要连接到远程主机，如果是第一次连接的话，远程主机会给出一个警告，并要求客户核对当前远程主机的公钥是否公示的公钥一致，如果一致的话，就可以进行登录了。

  - [x] [SSH原理与运用（一）：远程登录](http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html)

- [x] 了解postman 使用

  > [官网地址](https://www.postman.com/)，[postman软件下载地址](https://www.postman.com/downloads/)，[documentation](https://learning.postman.com/docs/getting-started/introduction/)