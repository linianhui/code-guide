# HTTP Method

面向资源设计的HTTP APIs中，绝大部分的操作都是`CRUD(Create,Read,Update,Delete)`，都可以映射为某一个[HTTP Method]。其余的无法映射的操作一般存在两种解决方案：

1. 抽象出新的资源，比如`禁用用户`的操作。假设用户的资源是`/users`，那么可以抽象出来一个被锁定的用户的资源`/users/disabled`。如此以来，
   1. `禁用用户`：`POST /users/disabled`或者`PUT /users/disabled/{user_id}`。
   2. `取消禁用`：`DELETE /users/disabled/{user_id}`。
   3. `获取被禁用的用户列表`：`GET /users/disabled`。
2. 如果上面的方式无法满足需要，则可以采用`POST`和`URL/动词`的组合。还拿上面的举例：
   1. `禁用用户`：`POST /users/{user_id}/disable`。
   2. `取消禁用`：`DELETE /users/{user_id}/disable`。
   3. `获取被禁用的用户列表`：`GET /users?status=DISABLED`。

## HTTP Method 语义列表

每一个`HTTP Method`都具有一下两个HTTP协议层面的语义。

| HTTP 语义 | 含义 |
|----------|-----|
| [安全]    | 操作不会对资源产生副作用，不会修改资源。|
| [幂等]    | 执行一次和重复执行N次，结果是一样的。|

## HTTP Method 列表

| HTTP Method | 安全 | 幂等 | 描述说明  |
|-------------|-----|-----|----------|
| [GET]       | ✔   | ✔   | 获取一个资源 | 
| [PUT]       | ✘   | ✔   | 更新或创建一个资源（完整替换） | 
| [PATCH]     | ✘   | ✘   | 更新一个资源（部分更新） | 
| [DELETE]    | ✘   | ✔   | 删除一个资源 |
| [POST]      | ✘   | ✘   | 创建，或者不满足以上四个Method语义的所有操作 |

>`PATCH`和`POST`都是`不安全`且`不幂等`的，差异在于`PATCH`仅是用于部分更新资源。`PATCH`是一个可选支持的`HTTP Method`，可能会存在一些代理、网关等组件不支持的情况，所以推荐用`POST`来代替它。

# 参考

https://tools.ietf.org/html/rfc7231#section-4

https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods


[HTTP Method]:https://tools.ietf.org/html/rfc7231#section-4

[安全]:https://tools.ietf.org/html/rfc7231#section-4.2.1

[幂等]:https://tools.ietf.org/html/rfc7231#section-4.2.2

[GET]:https://tools.ietf.org/html/rfc7231#section-4.3.1

[POST]:https://tools.ietf.org/html/rfc7231#section-4.3.3

[PUT]:https://tools.ietf.org/html/rfc7231#section-4.3.4

[DELETE]:https://tools.ietf.org/html/rfc7231#section-4.3.5

[PATCH]:https://tools.ietf.org/html/rfc5789
