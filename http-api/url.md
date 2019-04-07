# URL
URL遵循[RFC 3986]规范，由以下几部分组成。

<pre>
  https://api.linianhui.test:8080/user/disabled?first_name=li#title
  \___/  \______________________/\_____________/\___________/\____/
    |               |                   |             |          |
  scheme        authority              path         query    fragment
</pre>

URL的命名遵循[命名规范#URL][URL命名规范]的要求。

# 参考

https://tools.ietf.org/html/rfc3986

[RFC 3986]:https://tools.ietf.org/html/rfc3986
[URL命名规范]:name-case.md#url
