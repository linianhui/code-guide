# 参考

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
1. JSON Schema: http://json-schema.org/

格式化：
1. URI Template ( RFC6570 ) ：https://tools.ietf.org/html/rfc6570
1. Date and Time Formats - ISO 8601：https://www.w3.org/TR/NOTE-datetime
1. Date and Time on the Internet: Timestamps ( RFC 3339 ) ：https://www.ietf.org/rfc/rfc3339.txt


# HTTP APIs 规范指南

HTTP APIs的组成部分（`资源`，`URL`，`表述`，`JSON`）。
1. 基于`资源`设计API。
1. 基于`URL`标识`资源`。
1. 通过`URL`基于`表述`操作`资源`。
1. 基于`JSON`承载`表述`。
