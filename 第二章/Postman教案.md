# 第1节：Postman教案

## Postman简介

---
一般简单的接口测试我们可以直接在浏览器里面进行调试,但是涉及到一些权限设置的就无法操作了,因此我们需要接口测试的相关工具
Postman是一个接口测试和http请求的工具。

官网地址:<https://www.getpostman.com/>

Postman的优点:

* 支持各种的请求类型:get、post、put、 patch、 delete等
* 支持在线存储数据,通过账号就可以进行迁移数据
* 很方便的支持请求 header和请求参数的设置支持不同的认证机制,包括 Basic Auth, Digest Auth, OAuth1.0, OAuth2.0等
* 响应数据是自动按照语法格式高亮的,包括HTML,JSON和XML

## 下载安装

---
Postman有 windows,Mac、 Liunx以及 Chrome插件版本.这里主要介绍Wn平台版本的使用。

* 下载地址:<https://www.getpostman.com/downloads/>
* 官方文档<https://www.getpostman.com/docs/v6>
* PostmanApi文档:<https://docs.postman-echo.com>

## Postman 入门

---
安装好之后启动程序,进入主界面.准备开始使用 Postman

### 发送第一个请求

1. 启动软件后在引导界面点击 Request,给 Request命名然后创建文件夹并把该 Request归属到该文件夹
2. 在地址栏输λ入<http://postman-echo.com/get>然后点击Send按钮,可以看到返回值.如下图所示:
  ![](..\images\2get.png)

### Postman工作原理

如下图所示,当您在 Postman中输入请求并单击Send按钮时,服务器将接收您的请求并返回 Postman在接口中显示的响应。
![](..\images\2gzyl.jpg)

### Request编辑

在主界面左侧可以查看、保存、编辑 Request。

## 发送不同类型HTTP请求

---
### GET

HTTP GET请求方法用于从服务器检索数据。数据由唯一的URI(统一资源标识符)标识。
GET请求可以使用" Query String Parameters"将参数传递给服务器。例如,在下面的请求中,

     https://postman-echo.com/get?param1=51zxw&param2=66666

**请求说明**

* param1和 paran2表示发送的参数。
* ？后面接参数
* &连接多个参数

**参数编辑**

* 点击 Params按钮, Postman可以自动帮我们解析出对应参数。
* 如果想要暂时不传参数,可以方便的通过不勾选的方式去实现
* 如果想要批量的编辑参数,可以点击右上角的 Bulk edit,去实现批量编辑
  ![](..\images\2666.png)


**响应数据** 在主界面下方一栏菜单为响应菜单栏,可以查看响应内容, Cookie、 Headers、响应状态码等信息。
![](F:\gitbook\interfect51\images\26662.png)

返回值:
```json
{
    "args": {
        "param1": "51zxw",
        "param2": "66666"
    },
    "headers": {
        "x-forwarded-proto": "https",
        "host": "postman-echo.com",
        "accept": "*/*",
        "accept-encoding": "gzip, deflate",
        "cache-control": "no-cache",
        "content-type": "application/x-www-form-urlencoded",
        "cookie": "sails.sid=s%3ASuu380VNynx7t2iIbZ9kPtjU2k_OyZa8.O22iwzrXgNqEa%2BwqnJWtk3%2BDJ6H8A8l8cOU1tq64ta8",
        "postman-token": "69dd9cbe-fd85-46f1-a74c-57f6f4bc2c52",
        "user-agent": "PostmanRuntime/7.6.0",
        "x-forwarded-port": "443"
    },
    "url": "https://postman-echo.com/get?param1=51zxw&param2=66666"
}
```
### POST

HTTP POST请求方法旨在将数据传输到服务器,返回的数据取决于服务器的实现.POST请求可以使用 Query String Parameters以及body将参数传递给服务器。

**案例1**
在下面的请求中,使用 Query String Parameters传递参数。

    https://postman-echo.com/post?param=51zxw

返回值

```Python
{
    "args": {
        "param": "51zxw"
    },
    "data": "",
    "files": {},
    "form": {},
    "headers": {
        "x-forwarded-proto": "https",
        "host": "postman-echo.com",
        "content-length": "0",
        "accept": "*/*",
        "accept-encoding": "gzip, deflate",
        "cache-control": "no-cache",
        "content-type": "application/x-www-form-urlencoded",
        "cookie": "sails.sid=s%3ASuu380VNynx7t2iIbZ9kPtjU2k_OyZa8.O22iwzrXgNqEa%2BwqnJWtk3%2BDJ6H8A8l8cOU1tq64ta8",
        "postman-token": "43f4f7a1-f009-4d6c-ac29-817301d4b329",
        "user-agent": "PostmanRuntime/7.6.0",
        "x-forwarded-port": "443"
    },
    "json": null,
    "url": "https://postman-echo.com/post?param=51zxw"
}
```

**案例2**
发送一个 Request,其中body为 application/x-w-form- urlencode类型,参数分别为 param1=zxw和 param2=88请求URL如下:

    https://postman-echo.com/post

![](F:\gitbook\interfect51\images\2888.png)

</br>
**Postman Body数据类型说明: **

* **form- data multipart/form-data**是web表单用于传输数据的默认编码.这模拟了在网站上填写表单并提交它。表单数据编辑器允许我们为数据设置键-值对。
  我们也可以为文件设置一个键,文件本身作为值进行设置
* **x-www-form- urlencode**该编码与URL参数中使用的编码相同.我们只需输入键-值对, Postman会正确编码键和值.请注意,我们无法通过此编码模式上传文件。
  表单数据和 urlencode些差异,因此请务必首先检査AP的编码实现,确定是否可以使用这种方式发送请求。

* **raw**请求可以包含任何内容.除了替换环境变量之外, Postman不触碰在编辑器中输入的字符串。无论你在编辑区输λ什么内容,都会随请求一起发送到服务器。
  编辑器允许我们设置格式类型以及使用原始主体发送的正确请求头.我们也可以手动设置 Content-τype标题,这将覆盖 Postman定义的设置。

* **binary**二进制数据可让我们发送 Postman中无法输入的内容,例如图像,音频或视频文件。

返回值如下：
```json
{
    "args": {},
    "data": "",
    "files": {},
    "form": {
        "param1": "zxw",
        "param2": "888"
    },
    "headers": {
        "x-forwarded-proto": "https",
        "host": "postman-echo.com",
        "content-length": "21",
        "accept": "*/*",
        "accept-encoding": "gzip, deflate",
        "cache-control": "no-cache",
        "content-type": "application/x-www-form-urlencoded",
        "cookie": "sails.sid=s%3Af7j_I2DXNkNPWBUVT9XT2mZ0-AXvAcp1.Z%2FHWGX4aUsEJD1qrPrcKIWdEXOoraOawijr5WR%2BQW%2B0",
        "postman-token": "93ee3c1a-305e-4c0a-91d5-5cf73d0f601f",
        "user-agent": "PostmanRuntime/7.6.0",
        "x-forwarded-port": "443"
    },
    "json": {
        "param1": "zxw",
        "param2": "888"
    },
    "url": "https://postman-echo.com/post"
}
```

### PUT

HTTP PUT请求主要是从客户端向服务器传送的数据取代指定的文档的内容。
PUT请求可以使用 Query String Parameters以及body请求体将参数传递给服务器。

**案例:**
发送PUT请求,并传递字符参数"helo51zXW"

![](F:\gitbook\interfect51\images\2put.png)

    https://postman-echo.com/put
返回值
```Python
{
    "args": {},
    "data": "",
    "files": {},
    "form": {
        "hello 51zxw": ""
    },
    "headers": {
        "x-forwarded-proto": "https",
        "host": "postman-echo.com",
        "content-length": "11",
        "accept": "*/*",
        "accept-encoding": "gzip, deflate",
        "cache-control": "no-cache",
        "content-type": "application/x-www-form-urlencoded",
        "cookie": "sails.sid=s%3Akd-YyMn-jyqjGjB4Nr5QJdiB9EnB9YC5.kncHO6eRd5CzskO2O80q9mmBPSspnyMJUHl9eOFwXV0",
        "postman-token": "042d9f8e-e733-4c10-bd7c-533b2612bd95",
        "user-agent": "PostmanRuntime/7.6.0",
        "x-forwarded-port": "443"
    },
    "json": {
        "hello 51zxw": ""
    },
    "url": "https://postman-echo.com/put"
}
```

### DELETE

HTTP DElETE方法用于删除服务器上的资源, DELETE请求可以使用 Query String Parameters以及body请求体将参数传递给服务器。delete请求

    https://postman-echo.com/delete

返回值
```json
{
    "args": {},
    "data": "",
    "files": {},
    "form": {},
    "headers": {
        "x-forwarded-proto": "https",
        "host": "postman-echo.com",
        "accept": "*/*",
        "accept-encoding": "gzip, deflate",
        "cache-control": "no-cache",
        "content-type": "application/x-www-form-urlencoded",
        "cookie": "sails.sid=s%3AH98u5xdFDmcdwALUeuzPIDIwtw0BDDJg.E6fm%2FbBoe%2BgNKiUFNO%2Fhq4N9cOsdoAYpGtt54o1g6Zs",
        "postman-token": "339baf8e-85ee-406e-a552-455e251358f4",
        "user-agent": "PostmanRuntime/7.6.0",
        "x-forwarded-port": "443"
    },
    "json": null,
    "url": "https://postman-echo.com/delete"
}
```

## Request Header

---
Request Header(请求头)用来说明服务器要使用的附加信息,比较重要的信息有 Cookie、 Referer、User- Agent等。
在 Postman中可以在请求下方的 Headers栏目来设置,如下如图所示：
![](F:\gitbook\interfect51\images\2get66.png)

## Response Header

---
Response Header（响应头)其中包含了服务器对请求的应答信息,如 Content-Type、 Server、 Set-Cookie等,
在 Postman主界面下方 Headers或者 Postman Console界面都可以查看 Response Header信息。
![](F:\gitbook\interfect51\images\2par66.png)
Tps:通过 Postman Console可以看到每次请求的 Request Header详细信息,详见视频演示。

##授权设置
很多时候,出于安全考虑我们的接口并不希望对外公开。这个时候就需要使用授权( Authorization)机制授权过程验证您是否具有访问服务器所需数据的权限。
当您发送请求时,您通常必须包含参数,以确保请求貝有访问和返回所需数据的权限。Postman提供授权类型,可以轻松地在 Postman本地应用程序中处理身份
验证协议Postman支持的授权协议类型如下：

* No Auth
* Bearer Token 
* **Basic auth **
* **Digest Auth **
* **OAuth 1.0**
* OAuth 2.0
* **Hawk Authentication** 
* AWS Signature 
* NTLM Authentication [Beta]

这里主要介绍以上加粗的授权协议的使用。

![](F:\gitbook\interfect51\images\2posta.png)

### Basic auth

基本身份验证是一种比较简单的授权类型,需要经过验证的用户名和密码才能访问数据资源。这就需要我们输入用户名和对应的密码。
案例:请求URL如下,授权账号：

* 用户名: postman
* 密码password
* 授权协议为: Basic auth

    https://postman-echo.com/basic-auth

* 如果不输入用户名密码,直接使用GET请求,则会返回提示: Unauthorized
* 输入用户名密码,选择 Basic auth授权类型,则返回如下结果：

    {
    "authenticated": true
    }


### Digest Auth

Digestauth是一个简单的认证机制,最初是为HTTP协议开发的,因此也常叫做HTTP摘要。其身份验证机制非常简单,它采用哈希加密方法,以避免用明文传输用户的口令。
摘要认证就是要核实參与通信的两方都知道双方共享的一个口令。
</br>
当 server想要查证用户的身份,它产生一个摘要盘问( digest challenge),并发送给用户。典型的摘要盘问例如以下：

```
    Digest realme"iptel org",qops="auth, auth-int ",
    nonces ="dcd98b7102dd2fee8b11d0f600bfbece93", opaque"", algorithm=MD5
```
这里包含了一组参数,也要发送给用户.用户使用这些參数,来产生正确的摘要回答,并发送给 server.摘要盘问中的各个參数,其意义例如以下:

 **realm(领域)**:领域參数是强制的,在全部的盘问中都必须有.它是目的是鉴别SP消息中的机密。在SIP实际应用中,它通常设置为SP代理
 server所负责的域名。

**nonce(现时)**:这是由 server规定的数据字符串,在 server每次产生一个摘要盘问时,这个參数都是不一样的(与前面所产生的不会雷同)。
"现时"一般是由一些数据通过md5杂凑运算构造的.这种数据通常包含时间标识和 server的机密短语.这确保每一个"现时"都有一个有限的
生命期(也就是过了一些时间后会失效,并且以后再也不会使用),并且是独一无二的(即不论什么其他的 server都不能产生一个同样的"现时")。

**algorithm(算法)**:这是用来计算的算法.当前仅仅支持MD5算法。

**qop(保护的质量)**：这个參数规定 server支持哪种保护方案。 client能够从列表中选择一个。值auth表示仅仅进行身份查验,auth-int表示
进行查验外,另一些完整性保护.须要看更具体的描写叙述,请參阅RFC2617。

</br>
**案例**

请求URL如下

    https://postman-echo.com/digest-auth
摘牌配置信息如下:用户名密码和上面 basic auth一样
```
Digest username="postman", realm="Users",nonce="nilLiL0037PRRhofwdCLmw FsnEtHllew", uri="/digest-auth", 
response= "254679099562cf07df9b6f5d8d15db44",opaque=" "
```
![](..\images\2auth.png)


执行请求结果如下:
```
{
    "authenticated": true
}
```
</br>

## Hawk Auth

Hawk Auth是一个HTP认证方案,使用MAC( Message Authentication Code,消息认证码算法)算法,它提供了对请求进行部分加密验证的认证HTTP请求的方法。
hawk方案要求提供一个共享对称密匙在服务器与客户端之间,通常这个共享的凭证在初始TLS(安全传输层协议)保护阶段建立的,或者是从客户端和服务器都
可用的其他一些共享机密信息中获得的。

**案例**
请求URL如下:

    https://postman-echo.com/auth/hawk

密钥信息如下:
* Hawk Auth ID: dh37fg 492je 
* Hawk Auth Key: werxhqb98rpaxn39848xrunpaw3489ruxnpa98w4rxn 
* Algorithm; sha256
  ![](..\images\2hawk.png)


执行结果:
```
{
    "message":"Hawk Authentication Successful"
}
```
如果将key改为其他任意的字符则返回如下结果:

```
{
    "statuscode":401,
    "error":"Unauthorized", 
    "message":"Bad mac", 
    "attributes": {
        “error":"Bad mac”
    }
}
```

### OAuth 1.0

OAuth(开放授权)是—个开放标准,允许用户让第三方应用访问该用户在某一网站上存储的私密的资源(如照片,视频,联系人列表),
而无需将用户名和密码提供给第三方应。
</br>
用扩展资料

 * [OAuth那些事儿](https://blog.huoding.com/2010/10/10/8)
 * [OAuth的改变]（https://blog.huoding.com/2011/11/08/126）

**案例**
请求URL如下:请求方式为GET, Add authorization data to设置为: Request Headers

    https://postman-echo.com/oauth1
参数配置为

* Consumer Key: RKCGzna7bv9YD57c 
* Consumer Secret: D+EdQ-gs$-%@2Nu7
  ![](F:\gitbook\interfect51\images\2outh.png)

发送请求结果如下:
```
{
    "status":"pass", 
    "message":"0Auth-1ea signature verification was successful"
}
```
如果 Consumer Secret错误则返回如下结果

```
{
    "status":"fail",
    "message":"HMAC-SHAl verification failed", baseuri":https://postman-echo.com/oauth1,
     " normalized param string":
 " oauth_consumer _ey=51Zxw&oauth _nonce=pxSgzUivsB1&oauth _signature method=HMAC-SHA1&oauth timestamp=153129
9384&oauth version=1.0", 
        “base string”：
“ Get&httPs%3a%2f%2fpostman-    echo.com%2foauth1&oauthconsumerkey%3d51zxw%26oautHnonce%3dpxsgzuivsb1%26oau 
th _signature methodx3DHMAC-SHA1%26oauth timestamp%3D1531299384%26oauth version%3D1.0,
    "signing key":"DX2BEdQ-g5%24-%25%402Nu7&"
}
```
扩展资料:[各个授权协议文档](https://www.jellythink.com/archives/169)
</br>

## Cookie设置

---
cookie是存储在浏览器中的小片段信息,每次请求后都将其发送回服务器,以便在请求之间存储有用的信息。比如很多网站登录界面都有保留账号密码,以便下次登录。

由于HTTP是一种无状态的协议,服务器单从网络连接上无从知道客户身份。怎么办呢?就给客户端们颁发一个通行证吧,每人一个,无论谁访问都必须携带自己通行证。
这样服务器就能从通行证上确认客户身份了.这就是 Cookie的工作原理。

Cookie是由服务端生成,存储在响应头中,返回给客户端,客户端会将 cookie存储下来,在客户端发送请求时, user- agent会自动获取本地存储的 cookie,将 cookie信息
存储在请求头中,并发送给服务端. postman也可以设置、获取、删除 Cookie。
</br>

### Set Cookies

在Send按钮下方点击 Cookies文字菜单,弹出如下界面,然后可以设置 Cookie。
![](F:\gitbook\interfect51\images\2setck.png)

请求URL如下:请求方式为GET添加 Cookie值为 username:51zXw 

     http://www.baidu.com
打开 Console找到 Request Header可以看到自定义设置的 Cookie内容。
![](F:\gitbook\interfect51\images\251zx.png)

### Get Cookies 

Cookie获取比较简单,直接获取 Response Headers里面的set- cookie值即可,或者在主界面下方 Cookie菜单栏里面也可以查看。
![](F:\gitbook\interfect51\images\2getck.png)

### Delete Cookies

点击 Cookies文字菜单，然后可以根据需求去清除对应的 Cookie。

</br>

## 变量

---
### 问题思考

在开发不同阶段可能存在不同的环境比如测试环境和生产环境。

测试环境AP|如下：

    https://dev.postman.com/get
    https://dev.postman.com/get
    https://dev.postman.com/put

生产环境AP如下:

    https://postman-echo.com/get
    https://postman-echo.com/post
    https://postman-echo.com/put

在这么情况下,按照常规思路要么你需要维护两套环境的AP,要么毎次都手动一个个去修改URL,不管哪种选择都比较麻烦且低效,
那么有没有比较的好的方法来解决这个问题呢?

## Postman变量类型

通过比较我们可以发现,以上两组AP主要是除了host不同之外其他都一样,其实把Host用**变量**替换,这样就可以灵活切换环境。

Postman提供了变量设置,有4种变量类型。

* 本地变量( Localvariable)
* 全局变量( Global Variable
* 环境变量( Environment variable)
* 数据变量( Data Variable)
  </br>

  ### 环境变量

  环境变量指在不同环境,同一个变量值随着环境不同而变化,比如我们上面举例场景就可以使用环境变量,当在测试环境时,
  host值为:[dev.postman.com](http://dev.postman.com/),当切換到生产环境时,host值变为:[postman-echo.com](https://docs.postman-echo.com)

环境变量设置：在 postman界面点击右上角眼睛图标,即可开始设置环境变量和全局变量.环境变量设置过程如下图所示:
我们可以设置两种环境deν和 release. deν是开发测试环境; release是正式的生产环境.host环境变量,根据不同的环境值
不一样。
![](F:\gitbook\interfect51\images\2add.png)

![](F:\gitbook\interfect51\images\2add2.png)

![](F:\gitbook\interfect51\images\2add3.png)
详细过程见视频演示。

### 本地变量

本地变量主要是针对单个URL请求设置的变量,作用域只是局限在请求范围内。如请求URL如下,
设置两个本地变量( user, passwd)作为参数.请求方式为POST

     https://postman-echo.com/post
![](F:\gitbook\interfect51\images\2bb.png)

从上图中我们可以看到变量设置的格式为{{ variable name}}
变量设置好之后需要赋值,在pre- request- Script里面编写如下代码:

    pm variables.set( "user","51ZXW"); 
    pm variables.set("passwd","66666 ");
点击send执行之后的返回值如下,可以看到我们定义的变量已经发送。
![](F:\gitbook\interfect51\images\2bb1.png)
</br>

### 全局变量

全局变量是指在所有的环境里面,变量值都是一样的,全局变量的作用域是所有请求。
全局变量设置有两种方式:

* 点击界面里设置
* 在脚本里设置

**界面设置**

点击眼睛图标后,在 Global选项菜单点击εdit菜单即可设置全局变量,如下图所示.全局变量的引用格式和环境变量一样。
注意:当环境变量和全局变量名称一样时,切换到某个环境时,环境变量会覆盖全局变量。
![](F:\gitbook\interfect51\images\2ym.png)

**脚本设置**
使用如下脚本可以设置全局变量: variable key表示变量名称, variable_ value表示变量值。

    pm.globals.set("variable_key","variable_value");

**实践案例**
在实际接口测试过程中,接口经常会有关联。比如需要取上一个接口的某个返回值,然后作为参数传递到下一个接口作为参数。
假设我们要获取A接口返回的 userid值作为B接口的请求参数。
A接口请求URL如下：

    https://postman-echo.com/post

* 请求方式为Post
* 请求参数: userid(这里自己定义,接口会返回对应的id值)
  返回值
  ![](F:\gitbook\interfect51\images\2pp1.png)
  ![](F:\gitbook\interfect51\images\2pp2.png)
  根据返回值我们需要从返回值中提取 userid值。在τest标签栏下编写如下脚本获取υserid值
  ![](..\images\2pp3.jpg)

  B接口请求URL如下:请求方式为GET

    postman-echo.com/get?userid={{userid}}
  先执行A接口的,然后在执行B接口,此时B接口通过全局变量 userid可以获得A接口的返回值。
  </br>

数据变量
数据变量是通过导入外部数据文件(json文件或者csv文件),来获取变量数据。
我们可以创建一个如下内容的json文件:

**data. json**
![](F:\gitbook\interfect51\images\2pp4.png)
稍后我们会结合运行 Collection来讲解如何导入该数据文件。

## 断言

---
### 简介

一般来说执行完测试,我们需要对测试结果来进行校验,判断结果是是否符合我们的预期,也就是断言。
在接口测试中一般会根据响应状态码或者响应返回的数据来进行断言。

Postman提供一个测试沙箱( [Postman Sand box](https://learning.getpostman.com/docs/postman/scripts/postman_sandbox/))测试沙箱是一个 JavaScript执行环境,可以通过
JS脚本来编写pre- request Script和 test Script.

* pre-request Script(预置脚本)可以用来修改一些默认参数在请求发送之前执行.有点类似于 unittest里面的 setUp()方法。
* test Script(测试脚本)当接收到响应之后,再执行测试脚本。

### 案例

接口请求URL如下:请求方式为POST 

    postman-echo.com/post

**断言规则**
* 响应状态码:200
* 响应内容:返回的user参数值与定义的一致
* 响应时间:小于0.5s

**测试脚本**
在pre-request script定义变量user

    pm.variables.set("user",'zxw');
在Test栏下面编写如下脚本
![](index_files/b8c2b370-e55c-4b74-ba91-40ecbf30cfa8.jpg)

**断言结果**
![](index_files/1bd93d20-b96e-499e-a764-381662c766cb.png)

扩展资料: [Postman测试脚本官方文档](https://learning.getpostman.com/docs/postman/scripts/intro_to_scripts/)
</br>

##运行 Collection

---
### 批量执行

当我们想批量测试某个集合里面的各个API时,可以使用 Collection Runner来批量运行AP,同时可以进行环境
变量、迭代执行次数、延迟时间等设置。
![](index_files/83126d96-9a8d-4687-8897-10e2fba012aa.png)


执行结果
![](index_files/4a35b68b-243a-45a6-9b47-6971152ffa95.png)

## 数据驱动

### 应用背景

有时我们针对一个接口需要测试很多不同的参数,如果每次一个个的去修改参数值来进行测试这样效率肯定会比较低下。
因此我们需要每次迭代执行传入不同的参数进行测试,那么需要导入外部数据文件进行参数化,也就是所谓的数据驱动。

### 数据导入

如下图所示,data选择之前我们创建的json数据文件: data.json,文件类型选择 application/json json数据内容如下。

![](index_files/7bce4dcf-5a8a-4535-9756-6f18837af92c.png)
![](index_files/20d140ff-f6f9-4989-b8d3-61574c1eb3f5.png)
请求之前延迟时间最好设置为1000~3000,避免过于频繁请求被禁。
![](index_files/268a2f6c-69ce-4fd8-a349-8c460c0c1041.png)
点击 Preview按钮可以预览导入的数据。
![](index_files/57822120-b38c-4094-bd1f-56c6cf19f2bb.png)

### 执行结果

![](index_files/b05c7dea-641f-4093-bd0d-7492da779e55.png)

</br>

## 构建工作流

###问题思考
在使用" Collection runner"的时候,集合中的请求执行顺序就是请求在 Collection中的显示排列顺序。但是,有的时候我们不希望请求按照这样的方
式去执行,可能是执行完第一个请求,再去执行第五个请求,然后再去执行第二个请求这样的方式;那么在" Collection Runner"中如何去构建不同的执
行顺序呢?

### 设置方法

最直接的方法就是直接在集合里面拖动调整顺序,但是毎次去拖动也比较麻烦,特别是当请求比较多的时候.这时候最高效的方法就是通过脚本设置。
首先下载官方提供的案例文件:collection.json导入到 postman,运行Collection结果如下图所:
![](index_files/80f06d0b-1333-486f-8d05-3edf2aa11241.png)

接下来要调整执行顺序为: Request1-> Request3-> Request.2-> Request4
</br>
首先在第一个请求 Request1中Test添加如下代码:表示下一个请求为执行请求名称为 Request3的请求

    postman.setNextRequest('Request 3')
然后在 Request3的请求中Test添加如下代码:表示下一个请求为执行请求名称为 Request2的请求

    postman.setNextRequest('Request 3')
最后在 Request2的请求中Test添加如下代码:表示下一个请求为执行请求名称为 Request4的请求。

    postman.setNextRequest('Request 3')
注意:第一个执行请求的排序一定要在第一个
</br>
###执行结果
![](index_files/7118d47a-848b-457f-ac7b-5a5db4fce813.png)

相关资料: [collection runs官方文档](https://learning.getpostman.com/docs/postman/collection_runs/intro_to_collection_runs/)

</br>

## 命令执行

---
### 问题思考

在前面我们都是在 postman图形界面工具里面进行测试,但是有时候我们需要把测试脚本集成到CI平台,或者在非图形界面
的系统环境下测试,那么该如何处理呢?

### Newman简介

[Newman](https://www.npmjs.com/package/newman#using-newman-as-a-nodejs-module)是一款基于 Node. js:开发的可以运行 Postman的工具,使用 Newman,可以直接从命令行运行和测试Postman集合。

### Newman应用

**环境准备**

* Node.js
* cnpm或npm
  以上安装可以参考: [Appium环境搭建](https://www.51zxw.net/show.aspx?id=69959&cid=670)
  配置好环境后,执行如下命令安装 newman

    cnpm install newman --global
  输入如下面命令检测安装是否成功

    C: \Users\Shuqing>newman -v
    3.10.8

**执行测试**
首先将 postman的集合导出,如下图所示:
![](index_files/997ec11a-3554-4971-98da-1532e8d0df67.png)


在桌面新建文件夹 pmtest将导出的 postman文件和相关数据文件放入。
打开cmd进入到 pmtest目录,输入如下命令：

    newman run Postman_API. postman_collection.json -d data.json -r html
**命令说明**

* run代表要执行的 postman脚本,即为导出的集合。
* -d表示要执行的数据,也就是之前导入 postman的数据
* -r生成的测试报告类型这里生成html格式报告
  更多命令用法请输入 newman-h即可查看。

### 报告查看

在测试文件夹 pmtest里面可以看到生成的一个 newman文件夹,打开就可以看到生成的测试报。
Html报告样式:[newman-run-report ](https://sutune.oss-cn-shenzhen.aliyuncs.com/interface_test/Postman/newman-run-report.html)

newman不仅支持生成html报告,还支持其他报告类型:

* JSON reporter 
* JUNIT/XML reporter 
* Client repo
* Html report

</br>

## 集成 Jenkins 

---
### Jenkins简介

Jenkins是—个开源软件项目,是基于Java开发的_种[持续集成]工具,用于监控持续重复的工作,旨在提供一个开放易用的软件平台,
使软件的持续集成变成可能。

### 下载与安装

下载地址:<https://jenkins.io/download/>

下载后安装到指定的路径即可默认启动页面为 localhots:8080如果8080端口被占用无法打开,可以进入到 jenkins安装目录,找到 
jenkins.xm配置文件打开,修改如下代码的端口号即可。
![](index_files/cbcc3143-540f-411e-94ce-623ffdcb2a2b.png)

### 集成步骤

集成到 jenkins的思路其实很简单,就把之前我们执行测试的cmd命令放到 jenkins里面去执行。集成步骤也很简。

* 首先新建一个项目: postman_ api_test
* 然后在构建栏目下拉菜单选择 Execute windows batch command
  ![](index_files/4cb6aad0-ee45-4da6-b11a-866518aa2de6.png)
  Tips:我的 jenkins:安装在D盘因此需要使用命令c:切换到 postman脚本所在盘符。
  ![](index_files/dbde41f0-db8b-4faa-b446-fa1755c69807.png)
  最后执行结果如下：
  ![](index_files/34e345e2-9de3-41cd-bb22-b79cd48b716b.png)
  其他设置如设置定时执行,可以参考 Apium教程中的:[6-14框架综合实践(13) ——jenkins自动化测试平台搭建](https://www.51zxw.net/show.aspx?id=70266&cid=670)
  </br>

## 导出不同语言脚本

### 问题思考

虽然 Postman功能比较强大,但是毕竟是一款商业工具,多少会有一些限制.比如只支持js脚本运行,如果我们想用自己熟悉的
编程语言(如: Python java等)来做接口自动化测试该如何处理?

### 操作步骤

Postman支持导出不同语言版本的脚本,当一个接口调试好之后,点击右侧的code字样即弹出如下界面可以选择语言.最后选择
你需要语言版本即可生成对应的代码。
![](index_files/a353053f-7550-48b3-babc-e75ae0795f00.png)
生成的代码片段可以点击 Copy to Clipboard复制。
![](index_files/ef5ac5bc-2934-428d-b887-20365061d90e.png)

</br>

---
## 参考资料

* <https://docs.postman-echo.com/?version=latest#1eb1cf9d-2be7-4060-f554-73cd13940174>
* <https://www.jellythink.com/archives/169>
* <https://blog.csdn.net/wangyuquanliuli/article/details/24850761>
* <https://www.cnblogs.com/happy-today/p/7928822.html>
* <http://www.mamicode.com/info-detail-1693734.html>
* <https://blog.csdn.net/qq_14908027/article/details/77923792>












