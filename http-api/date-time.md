# 时间

时间采用[RFC 3339]中定义的通用的格式。表示方法如下：
| 格式              | 组成部分    | 示例   |
|------------------|-----------|-----------|
| `date-fullyear`  | 4位数的年份 | 2018 |
| `date-month`     | 2位数的月份 | 04     |
| `date-mday`      | 2位数的日期 | 01     | 
| `time-hour`      | 2位数的小时 | 02     |
| `time-minute`    | 2位数的分钟 | 08     |
| `time-second`    | 2位数的秒数 | 59     |
| `time-secfrac`   | 秒的分数部分 | .256    |
| `time-numoffset` | **+**/**-**`time-hour`**:**`time-minute` | +08:00 |
| `time-offset`    | **Z**/`time-numoffset` | Z+08:00 |
| `partial-time`   | `time-hour`**:**`time-minute`**:**`time-second time-secfrac` | 02:08:59.256 |
| `full-date`      | `date-fullyear`**-**`date-month`**-**`date-mday` | 2018-04-01 |
| `full-time`      | `partial-time time-offset` | 02:08:59.256+08:00 |
| `date-time`      | `full-date`**T**`full-time` | 2018-04-01T02:08:59.256Z+08:00 |

>扩展：`date-fullyear-month`(年月)可表示为`date-fullyear`**-**`date-month`，比如`2018-04`。

1. 日期和时间应该满足上面表格中定义的格式。
1. 优先采用UTC时间（即Z+00:00）。如没有跨时区的要求，则必须携带时区偏移信息，比如上面的`2018-04-01T02:08:59.256Z+08:00`。


# 参考

https://tools.ietf.org/html/rfc3339

https://www.w3.org/TR/NOTE-datetime


[RFC 3339]:https://tools.ietf.org/html/rfc3339

[Date and Time Formats]:https://www.w3.org/TR/NOTE-datetime
