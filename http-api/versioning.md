# 版本化
在`Level 2`的HTTP APIs中，虽然我们推荐也努力使得我们的APIs不做不兼容的改动，但是依然无法彻底的避免不兼容的升级。这就使得我们不得不进行对APIs进行版本管理。通常有以下**3**种方案：
1. URL
    ```http
    GET http://api.linianhui.com/v1/resources HTTP/1.1
    ```
1. Request Header
    ```http
    GET http://api.linianhui.com/resources HTTP/1.1
    Api-Version: v1
    ```
1. Request Header (Accept Header)
    ```http
    GET http://api.linianhui.com/resources HTTP/1.1
    Accept: application/vnd.v1+json
    ```
**在`Level 2`中优先推荐使用方案1**。理由是其更直观，便于实现，便于日志追踪。
