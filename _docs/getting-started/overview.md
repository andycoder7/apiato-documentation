---
title: "概览"
category: "开始"
order: 3
---

* [概览](#Quick-Overview)
  * [基础工作流](#basic-flow)
  * [一个简单的路由（Route）访问点（Endpoint）](#sample-route)
  * [一个简单的控制器（Controller）方法](#control-fun)
  * [一个简单的执行动作（Action）](#sample-action)
  * [一个简单的用户响应（Response）](#user-res)

<a name="Quick-Overview"></a>
## 概览

<a name="basic-flow"></a>
### 基础工作流

当一个 HTTP 请求被收到时，它首先会触发你预定义的访问点（Endpoint），每个访问点（Endpoint）都拥有自己的路由（Route）文件。

<a name="sample-route"></a>
#### 一个简单的路由（Route）访问点（Endpoint）

```php
<?php
$router->get('hello', [
    'uses' => 'Controller@sayHello',
]);
```

在用户发起一个请求 `[GET] www.api.apiato.com/v1/hello` 到访问点（Endpoint）之后，它会去调用定义好的控制器（controller）方法（`sayHello`）。

<a name="control-fun"></a>
#### 一个简单的控制器（Controller）方法

```php
<?php
class Controller extends ApiController
{
	public function sayHello(SayHelloRequest $request)
	{
            $helloMessage = Apiato::call(SayHelloAction::class);

            $this->json([
                $helloMessage
            ]);
	}
}
```

这个方法通过接受一个请求类 `SayHelloRequest` 来自动判断用户是否具有权限。
_仅当用户具有权限时，它才会进入函数体继续执行。_

之后这个方法调用一个执行动作（Action）(`SayHelloAction`) 来处理业务逻辑。

<a name="sample-action"></a>
#### 一个简单的执行动作（Action）

```php
<?php
class SayHelloAction extends Action
{
	public function run()
	{
	    return 'Hello World!';
	}
}
```

在执行动作（Action）中可以做任何事情，然后返回一个结果（结果可以是一个对象，也可以是字符串或者任何内容）。

当执行动作（Action） 执行完毕，控制器（Controller）方法会准备好构建一个请求响应（Response）。

可以通过工具方法 `json` (`$this->json(['foo' => 'bar']);`) 来构建 Json 格式的请求响应（Responses）。

<a name="user-res"></a>
#### 一个简单的用户响应（Response）

```json
[
    "Hello World!"
]
```
