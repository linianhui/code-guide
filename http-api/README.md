# HTTP APIs 规范指南

HTTP APIs的组成部分（`资源`，`URL`，`表述`，`JSON`）。
1. 基于`资源`设计API。
1. 基于`URL`标识`资源`。
1. 通过`URL`基于`表述`操作`资源`。
1. 基于`JSON`承载`表述`。

>根据REST APIs的成熟度模型  
>![REST APIs 成熟度模型](imgs/richardson-maturity-model.png)  
>此规范关注的是`Level 2`的APIs。


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

