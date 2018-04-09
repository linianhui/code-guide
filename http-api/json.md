# JSON
[JSON]是一种应用非常广泛的数据交换格式。其包含6种基本的数据类型。

| JSON数据类型 |  示例 |
|------------ |-------|
| `string`    | "lnh" |
| `number`    | 1.23  |
| `array`     | [...]    |
| `object`    | {...}    |
| `bool`      | true/false |
| `null`      | null |

1. JSON的命名遵循[命名规范#JSON][JSON命名规范]。
1. JSON中没有原生的日期和时间类型，应该遵循[日期和时间的格式化规范][Date Time]的要求，使用`string`类型表示。
1. JSON中出现的和国际化相关的数据遵循[国际化规范][i18n]中的要求。
1. `null`值的字段不能忽略掉，应该显式的表示为`"field_name":null`。

JSON示例：
```json
{
  "first_name": "li",
  "lase_name": "nianhui",
  "gender": "MALE",
  "age": 123,
  "tags": ["coder"],
  "is_admin": true,
  "address": null,
  "country_code":"CN",
  "currency_code":"CNY",
  "language_code":"zh",
  "locale_code":"zh-CN",
  "created_at":"2018-01-02T03:04:05.128Z+08:00",
  "time_zone":"+08:00"
}
```

# 参考资料
http://json.org/

https://tools.ietf.org/html/rfc7159

[JSON]:http://json.org/
[JSON命名规范]:name-case.md#json
[Date Time]:date-time.md
[i18n]:i18n.md
