# 命名规则

| 规则名称                     | 说明               | 取值范围 |
|-----------------------------|--------------------|--------|
| `all-lower-hyphen-case`     | 采用`-`分隔符的全小写 | `a-z 0-9 -`|
| `all_lower_underscore_case` | 采用`_`分隔符的全小写 | `a-z 0-9 _`|
| `ALL_UPPER_UNDERSCORE_CASE` | 采用`_`分隔符的全大写 | `A-Z 0-9 _`|

## URL

| URL组件    | 命名规则                     |
|-----------| ----------------------------|
| scheme    | `all-lower-hyphen-case`     |
| authority | `all-lower-hyphen-case`     |
| path      | `all-lower-hyphen-case`     |
| query     | `all_lower_underscore_case` |
| fragment  | `all-lower-hyphen-case`     |

>URL的query部分是`name=value`而不是`key=value`，URL支持name重复存在，Web服务端框架绝大部分都支持直接映射为数组。此外命名规则约束的是`name`部分，而不关心`value`部分，`value`部分应该采用`urlencode`进行编码。

示例：`https://api.my-server.com/v1/user-stories?dipplay_names=abc&display_names=efg`，服务端会得到一个类型为数组的`dispaly_names`参数。
```json
display_names = [
  "abc",
  "efg"
];
```

## JSON

| JSON              | 命名规则                     |
|-------------------| ----------------------------|
| filed_name        | `all_lower_underscore_case` |
| filed_value       | 无要求                       |
| ENUM_FILED_VALUE  | `ALL_UPPER_UNDERSCORE_CASE` |

>`ENUM_FILED_VALUE`用于表示枚举字段，用全大写和`_`分隔符，以示和普通的字符串进行区分。

示例：

```json
{
  "first_name":"li",
  "lase_name":"nianhui",
  "gender":"MALE",
  "remark":"描述信息",
  "age":1234
}
```
# 参考

https://support.google.com/webmasters/answer/76329

https://stackoverflow.com/questions/5543490/json-naming-convention

https://tools.ietf.org/html/rfc3986#section-2.4
