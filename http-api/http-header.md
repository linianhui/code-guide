# HTTP Headers

Http Header的用途在于携带`HTTP Request`和`HTTP Response`的元数据信息的`Name:Value`数据(Name不区分大小写，通常都采用首字母大写，`-`分隔的写法，比如`Content-Type`)。按其用途可以分为如下4类：

1. 通用类：描述请求和响应的。
2. 请求类：描述请求的。
3. 响应类：描述响应的。
4. 表述类：描述请求和响应的`Body`部分的。

HTTP APIs中常用到的Headers：

| Header             | 描述说明                       | 示例  |
|--------------------|-------------------------------|------|
| [Accept]           | 客户端期望服务器返回的数据格式。   | `Accept:application/json` |
| [Accept-Charset]   | 客户端期望服务器返回的数据的字符集。| `Accept-Charset:utf-8` |
| [Content-Type]     | 描述`Body`的数据类型。           | `Content-Type:application/json`
| [Content-Encoding] | 描述`Body`的编码方式。           | `Content-Encoding: gzip`|
| [Content-Length]   | 描述`Body`的长度。              | `Content-Length: 1234`|
| [Location]         | `Response`中提供给客户端的连接   | `Location: /user/1`|

## 示例

HTTP Request:
```http
POST /xxx HTTP/1.1
Accept: application/json;
Accept-Charset: utf-8
Content-Type: application/json;charset=utf-8

{
  "x":1,
  "y":2
}
```

HTTP Response:
```http
HTTP/1.1 201 Created
Content-Type: application/json;charset=utf-8
Content-Encoding: gzip
Location: /xxx/1
Request-Id: {id}

```

>`Request-Id`可以由`Http Request`传入，也可以由服务端生成，追加此信息到`log`中，便于服务端追踪请求。

# 参考

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers

https://tools.ietf.org/html/rfc7231#section-5

https://tools.ietf.org/html/rfc7231#section-7


[Accept]:https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept

[Accept-Charset]:https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Charset

[Content-Type]:https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type

[Content-Encoding]:https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Encoding

[Content-Length]:https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Length

[Location]:https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Location
