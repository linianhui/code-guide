# 错误处理
虽然`HTTP Stauts Code`有`4xx`和`5xx`的状态码来表示哪里出错了，但是其代表的只是`HTTP协议层面`的错误描述，它无法提供和业务相关的更具体错误描述。基于此种情况，我们需要设计一套描述业务层面错误的数据结构：

```json
[
  {
    "error": "user_name",
    "message": "用户名不能为空。"
  },
  {
    "error": "age",
    "message": "用户年龄不能小于0。"
  }
]
```

1. 这个数据结构仅在状态码为`4xx`和`5xx`出现的时候才会使用；`2xx`的时候则不包含此数据结构。
2. `error`字段可以是一些出错的字段名、某一错误类别（比如`no_permission`）等等。
    ```json
    [
      {
        "error": "no_permission",
        "message": "没有user.delete的权限"
      }
    ]
    ```

# 参考

Problem Details for HTTP APIs : https://tools.ietf.org/html/rfc7807
