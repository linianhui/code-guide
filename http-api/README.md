# Moved to https://linianhui.github.io/code-guide/

# HTTP APIs 设计/规范指南

根据REST APIs的成熟度模型 ，此规范关注的是`Level 2`的APIs。
![REST APIs 成熟度模型](img/richardson-maturity-model.png)  

# 1 设计指南

HTTP APIs主要由四部分组成：`HTTP`,`URL`,`资源`，`资源的表述(JSON)`。资源的表述格式通常都采用`JSON`，故而后面就使用`JSON`代指`资源的表述`。根据这些组成部分，按照以下**3**个步骤设计APIs：
1. 基于`资源`设计APIs。
1. 基于`URL`标识`资源`。
1. 基于`JSON`和`HTTP`操作`URL`标识的`资源`。

## 1.1 基于`资源`设计API

设计HTTP APIs的首要任务是识别出业务领域中存在的资源。资源是对服务端提供的服务进行分解、组合后的一个被命名的抽象概念。

>有一个很重要的点需要明确一下：资源**≠**数据表，它们两个之间并没有直接的映射关系。如果直接把数据存储结构映射为资源，则只会让资源无法有效的表达业务需要，也会造成资源本身和底层存储的紧耦合。

资源的设计是以`名词`为中心的。比如`今天的天气`是一个资源；而`获取今天的天气`则不是，它代表的是对`今天的天气`资源的一个读取操作。基于此我们可以抽象出来一个`天气`的资源。

## 1.2 基于`URL`标识`资源`

识别出`资源`后，则需要为其分配一个`URL`进行标识。
1. 一个`资源`可以有多个`URL`。
1. 一个`URL`只能标识一个`资源`。
>总结来说就是`资源`:`URL`的关系就是`1:N`的关系。

比如上面提到的`天气`和`今天的天气`这两个资源，可以用如下的`URL`进行标识。

| 资源       | URL                                     |
| ---------- | --------------------------------------- |
| 天气       | `/weather`                              |
| 今天的天气 | `/weather/today`                        |
| 今天的天气 | `/weather/2018-04-01`，今天是2018-04-01 |

`资源`体现在`URL`中的`Path`部分。
>关于资源名采用单数还是复数的问题，这里统一为单数（即使代表的是一个集合资源）。原因有3：
>   1. 一致性：中文中并无复数的概念，可保持一致。
>   2. 无二义性：比如news，既是单数也是复数。所以就不必追求它们的单数或者复数形式形式；基于同样的原则，那么原本就是单数的名词，也无需刻意追求复数形式。
>   3. 简单性：英文名词的复数形式并不统一（比如order > orders, history > histories）,使用单数可以避免团队成员对于这些差异的不同理解与争执。

`资源`存在子资源的情况下，可以把子资源提升为顶层的资源。比如有一个订单资源`/order/{order_id}`，订单中包含2件物品。
```
# 不推荐 单个子资源
/order/{order_id}/item/{item_id}

# 推荐 单个子资源
/order-item/{order_item_id}

# 推荐 子资源集合
/order/{order_id}/item
```
## 1.3 基于`JSON`和`HTTP`操作`URL`标识的`资源`

在标识出`资源`以后，就可以使用`HTTP`通过`JSON`来操作资源了。
1. 使用`HTTP Method`来映射对资源的操作请求（CRUD或者其他）。
2. 使用`HTTP Header`携带请求/响应所需的元数据信息。
3. 使用`HTTP Stauts Code`代表`HTTP协议层面`的响应状态。
4. 使用`JSON`作为数据交换格式。

# 2 规范指南

## 2.1 通用部分 
1. [HTTP Method 规范][HTTP Method]
1. [HTTP Header 规范][HTTP Header]
1. [HTTP Stauts Code 规范][HTTP Stauts Code]
1. [URL 规范][URL]
1. [JSON 规范][JSON]
1. [命名（URL和JSON）规范][Name Case]
1. [日期和时间格式化 规范][Date Time]
1. [国际化 规范][i18n]
1. [版本化 规范][versioning]
1. [错误处理 规范][error]


## 2.2 Request 公共查询参数

| 参数用途 | 参数名                                         | 取值范围                                              |
| -------- | ---------------------------------------------- | ----------------------------------------------------- |
| 分页     | `page`<br/>`page_size`                         | >=1                                                   |
| 排序     | `sort`                                         | `{field_name}\|{asc\|desc},{field_name}\|{asc\|desc}` |
| 区间     | `{field_name}_before`<br/>`{field_name}_after` | 无要求                                                |
| 时间     | `{field_name}_at`                              | 无要求                                                |

示例:
```http
GET /user
    ?page=2
    &page_size=10
    &sort=name,age|desc
    &created_at_after=2018-01-01
    &created_at_before=2018-06-01
```

上面的查询代表的含义：按照`name`升序和`age`倒序的排序方式；获取`created_at`时间位于`2018-01-01`和`2018-06-01`区间内；按照每页`10`条数据，获取第`2`页的数据。

## 2.3 Response 分页数据结构

在分页请求的时候，API会返回分页后的数据和分页的信息。
```json
{
  "page": 2,
  "page_size": 10,
  "total_count": 100,
  "items":[
    {...},
    {...},
  ]
}
```
# 3 示例

... 待补充

# 参考资料

PayPal的API设计指南：https://github.com/paypal/api-standards

REST架构风格的出处：架构风格与基于网络的软件架构设计(by Fielding, R.)论文。
1. 英文版： https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm
1. 中文版： http://www.infoq.com/cn/minibooks/web-based-apps-archit-design
1. 本人的解读REST系列博客：http://www.cnblogs.com/linianhui/category/774322.html

HTTP APIs 四大组成部分（HTTP,URI,MIME,JSON）
1. HTTP/1.1 ( RFC7230-7235 ) ：https://tools.ietf.org/html/rfc7230
1. URI ( RFC 3986 ) ：https://tools.ietf.org/html/rfc3986
1. MIME ( RFC 2387 )：https://tools.ietf.org/html/rfc2387
1. JSON : http://json.org/

Hypermedia
1. JSON Schema: http://json-schema.org/

URL模板
1. URI Template ( RFC6570 ) ：https://tools.ietf.org/html/rfc6570

时间日期格式化
1. Date and Time Formats - ISO 8601：https://www.w3.org/TR/NOTE-datetime
1. Date and Time on the Internet: Timestamps ( RFC 3339 ) ：https://tools.ietf.org/html/rfc3339#section-5.6

国际化
1. https://www.iso.org/iso-3166-country-codes.html
1. https://www.iso.org/iso-4217-currency-codes.html
1. https://www.iso.org/iso-639-language-codes.html

REST APIs 成熟度模型：https://martinfowler.com/articles/richardsonMaturityModel.html

[HTTP Header]:http-header.md
[HTTP Method]:http-method.md
[HTTP Stauts Code]:http-status-code.md
[Name Case]:name-case.md
[Date Time]:date-time.md
[URL]:url.md
[JSON]:json.md
[i18n]:i18n.md
[versioning]:versioning.md
[error]:error.md
