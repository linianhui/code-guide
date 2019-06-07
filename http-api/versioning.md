# 版本化

在`Level 2`的HTTP APIs中，虽然我们推荐也努力使得我们的APIs不做不兼容的改动，但是依然无法彻底的避免不兼容的升级。这就使得我们不得不对APIs进行版本化管理。通常有以下 **3** 种方案：

1. URL
    ```http
    GET http://api.linianhui.com/v1/weather HTTP/1.1
    ```
2. Request Header
    ```http
    GET http://api.linianhui.com/weather HTTP/1.1
    Api-Version: v1
    ```
3. Request Header (Accept Header)
    ```http
    GET http://api.linianhui.com/weather HTTP/1.1
    Accept: application/vnd.v1+json
    ```

**在`Level 2`的API中优先推荐使用方案1(`URL`)**。理由是其更直观，便于实现，便于日志追踪。
