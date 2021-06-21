# Linux

可以掌握常用工具的日常使用场景：

- [ ] awk统计ip，grep ，find ，curl

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

- [ ] 了解：logrotate，rsync

  - [ ] logrotate
  - [ ] rsync

- [ ] 掌握ansible基本用法：主要用于批量查日志，执行命令。

  > [Ansible中文权威指南](https://ansible-tran.readthedocs.io/en/latest/index.html)

Http：

- [ ] 常用header: Host

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

- [ ] 跨域 Cookie

  > [COOKIE跨域获取问题](https://segmentfault.com/a/1190000039227924)

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

  - [ ] merge 

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
    > **how to fix merge conflict:**
    >
    > 

  - [ ] rebase

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
    > ![](C:\Users\ASUS\OneDrive\程序员文件夹\微信截图_20210621152126.png)
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

  - [ ] revert 

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

  - [ ] cherry-pick

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