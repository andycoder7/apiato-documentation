---
title: "请求"
category: "开始"
order: 4
---

* [表单内容类型](#form-content-types)
* [HTTP 请求头部](#send-http-req)
* [调用访问点（Endpoint）](#call-EP)
  * [调用未保护的访问点（endpoint）示例](#call-unprotected-EP)
  * [调用受保护的访问点（endpoint）示例 (通过 Bearer 令牌来保护) ](#call-protected-EP)

<a name="form-content-types"></a>
## 表单内容类型 (W3C)

Apiato 默认使用 `x-www-form-urlencoded` 来编码简单的 文本/ASCII 数据，当然，它也支持其他类型。

#### ASCII 负载

你需要把 `Content-Type : x-www-form-urlencoded` 放在你的请求头部，来告诉网站服务器你使用的是简单的 文本/ASCII 负载编码 (`name=Mahmoud+Zalt&age=18`)。

#### JSON 负载

你需要吧 `Content-Type = application/json` 放在你的请求头部，来告诉网站服务器你使用的是 JSON 格式的负载编码 (`{name : 'Mahmoud Zalt', age: 18}`)。

*(你如果希望在本例中返回的数据格式也是 JSON。你可以把响应的序列化器从 `DataArraySerializer` 改为 `JsonApiSerializer`，更多信息请查看响应章节).*

<a name="send-http-req"></a>
## HTTP 请求头部

| 头部          |  内容示例                             | 什么情况下需要使用                                                              |
|---------------|-------------------------------------|------------------------------------------------------------------------------|
| Accept        | `application/json`                  | 每次向访问点（endpoint）发送时都必须带上                                              |
| Content-Type  | `application/x-www-form-urlencoded` | 每次传输数据时都必须带上                                                         |
| Authorization | `Bearer {Access-Token-Here}`        | 只要访问点（endpoint）需要权限认证时，就必须带上                                      |
| If-None-Match | `811b22676b6a4a0489c920073c0df914`  | 当指向一个先前请求的特定 **ETag** 时，应当带上。如果两个 ETag 同时匹配上，那么将会返回 HTTP 304（未修改）|


> #### 注意！
>
> 通常来说，当你调用一个 JSON API 时，你应该在 HTTP 头部包含 `Accept : application/json`。 
> 然而，在 Apiato 中，你可以通过在 `app/Ship/Configs/apiato.php` 里设置 `'force-accept-header' => true,` 
> 来强制你的用户发送 `application/json`，或者通过设置 `'force-accept-header' => false,` 来允许你的用户自行决定。
> 默认情况下，这个参数被设置为 false。

<a name="call-EP"></a>
## 调用访问点（Endpoint）

<a name="call-unprotected-EP"></a>
### 调用未保护的访问点（endpoint）示例：

```shell
curl -X POST -H "Accept: application/json" -H "Content-Type: application/x-www-form-urlencoded; -F "email=admin@admin.com" -F "password=admin" -F "=" "http://api.domain.test/v2/register"
```

<a name="call-protected-EP"></a>
### 调用受保护的访问点（endpoint）示例 (通过 Bearer 令牌来保护) ：

```shell
curl -X GET -H "Accept: application/json" -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..." -H "http://api.domain.test/v1/users"
```
