# HTTP APIs 规范指南

根据REST APIs的成熟度模型 ，此规范关注的是`Level 2`的APIs。
![REST APIs 成熟度模型](imgs/richardson-maturity-model.png)  

# 设计步骤

HTTP APIs主要由四部分组成：`资源`，`URL`，`表述`，`JSON`。每一个步骤都会涉及到其中的某一个组成部分。
1. 基于`资源`设计API。
1. 基于`URL`标识`资源`。
1. 通过`URL`基于`表述`操作`资源`。
1. 基于`JSON`承载`表述`。

## 1.基于`资源`设计API

设计HTTP APIs的首要任务是识别出当前业务领域中存在的资源。资源是对服务端提供的服务进行分解、组合的一个被命名的抽象概念，有一个很重要的点去要明确：资源**≠**数据表，它们两个之间并不是之间的映射关系。资源是一个业务层面的抽象概念，而非关于数据如何组织存储的。资源的设计是以`名词`为中心的，比如`今天的天气`是一个资源；而`获取今天的天气`则不是，它代表的是对`今天的天气`资源的一个读取操作。基于此我们可以再抽象出来一个`天气`的资源。

## 2.基于`URL`标识`资源`

标识出了资源以后，则需要为其分配一个[URL]进行标识。一个资源可以由多个`URL`，就像一个人可以姓名，绰号，乳名等等；但是一个`URL`只能标识一个资源。比如上面提到的`天气`和`今天的天气`这两个资源，可以用如下的`URL`进行标识。

| 资源      | URL               |
|----------|-------------------|
| 天气      | `/weathers`       |
| 今天的天气 | `/weathers/today` |
| 今天的天气 | `/weathers/2018-04-01`，今天是2018-04-01 |

`资源`体现在[URL]中的`Path`部分；遵循[命名规则]中的`URL`部分的命名的要求；并且如果资源代表的是一个集合，则以复数的形式出现。

`资源`的存在子资源的情况下，可以提取把子资源提升为顶层的资源。比如有一个订单资源`/orders/{order_id}`，订单中包含2件物品。
```
# 不推荐 单个子资源
/orders/{order_id}/items/{item_id}

# 推荐 单个子资源
/order-items/{order_item_id}

# 推荐 子资源集合
/orders/{order_id}/items
```

...未完成

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

REST APIs 成熟度模型
1. https://martinfowler.com/articles/richardsonMaturityModel.html


[HTTP Header]

[HTTP Method]

[HTTP Stauts Code]

[URL]

[命名规则]

[国际化]

[HTTP Header]:http-header.md
[HTTP Method]:http-method.md
[HTTP Stauts Code]:http-status-code.md
[URL]:url.md
[命名规则]:name-case.md
[国际化]:i18n.md

