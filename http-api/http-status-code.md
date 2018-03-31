# HTTP Status Code

[HTTP Status Code]用来指示`HTTP协议层面的请求状态`。它由一个数字和一个描述消息构成，比如`200 OK`。有以下几类状态码。
1. `2xx`：执行成功。
2. `4xx`：客户端的错误，通常情况下客户端需要修改请求然后再次发送请求。
3. `5xx`：服务端的错误。

| Status Code                  | 描述说明 |
|------------------------------|---------|
| [200 OK]                     | 执行成功。 |
| [201 Created]                | 资源创建成功，应该在`HTTP Response Header`中返回`Location`来提供新创建资源的URL地址。 |
| [202 Accepted]               | 服务端已经接受了请求，但是并未处理完成，适用于一些异步操作。 |
| [204 No Content]             | 执行成功，但是不会在`HTTP Response Body`中放置数据。 |
| [400 Bad Request]            | 客户端请求错误，客户端应该根据`HTTP Response Body`中的错误描述来修改请求，然后才能再次发送。 |
| [401 Unauthorized]           | 客户端未提供授权信息。 |
| [403 Forbidden]              | 客户端无权访问（客户端可能已经提供了授权信息，但是权限不够）。如果出于信息隐藏的目的，也可以使用`404 Not Found`来替代。|
| [404 Not Found]              | 客户端请求的资源不存在。 |
| [405 Method Not Allowed]     | 客户端使用了不被允许的HTTP Method。比如某一个URL只允许`POST`,但是客户端采用了`GET`。 |
| [406 Not Acceptable]         | 客户端发送的`Accept`不被支持。比如客户端发送了`Accept:application/xml`，但是服务器只支持`Accept:application/json`。 |
| [409 Conflict]               | 客户端提交的数据过于陈旧，和服务端的存在冲突，需要客户端重新获取最新的资源再发起请求。 |
| [415 Unsupported Media Type] | 客户端发送的`Content-Type`不被支持。比如客户端发送了`Content-Type:application/xml`，但是服务器只支持`Content-Type:application/json`。 |
| [429 Too Many Requests]      | 客户端在指定的时间内发送了太多次数的请求。用于限速，比如只允许客户端在1分钟内发送100次请求，客户端在发送101次请求的时候，会得到这样的响应。 |
| [500 Internal Server Error]  | 服务器遇见了未知的内部错误。 |
| [501 Not Implemented]        | 服务器还未实现次功能。 |
| [503 Service Unavailable]    | 服务器繁忙，暂时无法处理客户端的请求。 |

# 参考

https://tools.ietf.org/html/rfc7231#section-6

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

https://httpstatuses.com/

[HTTP Status Code]:https://tools.ietf.org/html/rfc7231#section-6

[200 OK]:https://tools.ietf.org/html/rfc7231#section-6.3.1

[201 Created]:https://tools.ietf.org/html/rfc7231#section-6.3.2

[202 Accepted]:https://tools.ietf.org/html/rfc7231#section-6.3.3

[204 No Content]:https://tools.ietf.org/html/rfc7231#section-6.3.5

[400 Bad Request]:https://tools.ietf.org/html/rfc7231#section-6.5.1

[401 Unauthorized]:https://tools.ietf.org/html/rfc7235#section-3.1

[403 Forbidden]:https://tools.ietf.org/html/rfc7231#section-6.5.3

[404 Not Found]:https://tools.ietf.org/html/rfc7231#section-6.5.4

[405 Method Not Allowed]:https://tools.ietf.org/html/rfc7231#section-6.5.5

[406 Not Acceptable]:https://tools.ietf.org/html/rfc7231#section-6.5.5

[409 Conflict]:https://tools.ietf.org/html/rfc7231#section-6.5.8

[415 Unsupported Media Type]:https://tools.ietf.org/html/rfc7231#section-6.5.13

[429 Too Many Requests]:https://tools.ietf.org/html/rfc6585#section-4

[500 Internal Server Error]:https://tools.ietf.org/html/rfc7231#section-6.6.1

[501 Not Implemented]:https://tools.ietf.org/html/rfc7231#section-6.6.2

[503 Service Unavailable]:https://tools.ietf.org/html/rfc7231#section-6.6.4
