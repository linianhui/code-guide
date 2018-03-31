# URL 组成部分
URL遵循[RFC 3986]规范，由以下几部分组成。

<pre>
  https://api.linianhui.test:8080/users/disabled?first_name=li#title
  \___/  \______________________/\_____________/\____________/\____/
    |               |                   |             |          |
  scheme        authority              path         query    fragment
</pre>

# 参考

https://tools.ietf.org/html/rfc3986

[RFC 3986]:https://tools.ietf.org/html/rfc3986