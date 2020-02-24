---
title: "响应"
category: "开始"
order: 5
---

* [Apiato 响应（Response）](#Res-payload)
* [默认 Apiato 响应（Response）内容](#Def-Res-payload)
* [修改默认响应（Response）内容](#change-apiao-res-payload)
* [资源密钥](#Resource-Keys)
* [错误响应（Response）格式](#Error-Res-Format)
* [在控制器（Controller）中构建一个响应（Response）](#build-res-from-con)

<a name="Res-payload"></a>
### Apiato  响应（Response）

在 Apiato 中，你可以自定义你的响应（Response）内容，或者使用框架中已经提供的序列化器之一。

当前已经提供的序列化器包括： (`ArraySerializer`, `DataArraySerializer` 和 `JsonApiSerializer`)。通过 [Fractal](http://fractal.thephpleague.com/transformers/) 提供。

默认情况下 Apiato 使用 `DataArraySerializer`。 下面是一个响应（Response）内容的例子

<a name="Def-Res-payload"></a>
### 默认 Apiato 响应（Response）内容：

`DataArraySerializer` 响应（Response）内容看上去就像这样：

```json
{
  "data": [
    {
      "id": 100,
      ...
      "relation 1": {
        "data": [ // 多重、复杂的数据
          {
            "id": 11,
			  ...
          }
        ]
      },
      "relation 2": {
        "data": { // 单一、简单的数据
          "id": 22,
          ...
          }
        }
      }
    },
    ...
  ],
  "meta": {
    "pagination": {
      "total": 999,
      "count": 999,
      "per_page": 999,
      "current_page": 999,
      "total_pages": 999,
      "links": {
        "next": "http://api.apiato.test/v1/accounts?page=999"
      }
    }
  },
  "include": [ // 什么可以被包含
    "xxx",
    "yyy"
  ],
  "custom": []
}
```

**分页的响应：**

当数据已经被分页处理时，响应的内容将包含一个 `meta` 字段来描述分页信息。

```json
{
  "meta": {
    "pagination": {
      "total": 999,
      "count": 999,
      "per_page": 999,
      "current_page": 999,
      "total_pages": 999,
      "links": {
        "next": "http://api.apiato.test/v1/accounts?page=999"
      }
    }
  },
  "include": [ // 什么可以被包含
    "xxx",
    "yyy"
  ],
  "custom": []
}
```

**Includes 字段说明：**

通知用户在这个响应（Response）中，什么关系数据是可以被包含的。例如：`?include=tags,user`

更多信息可以阅读 [请求参数]({{ site.baseurl }}{% link _docs/features/query-parameters.md %}) 页面的 `关联关系` 一节。

<a name="change-apiao-res-payload"></a>
### 修改默认响应（Response）内容：

默认情况下，响应（Response）的格式处理被指定为 `DataArray` Fractal Serializer (`League\Fractal\Serializer\DataArraySerializer`)。

你可以打开 `app/Ship/Configs/fractal.php` 文件来修改默认的 Fractal Serializer。

```text
'default_serializer' => League\Fractal\Serializer\DataArraySerializer::class,
```

支持的序列化器（Serializers） 包括：
* `ArraySerializer`
* `DataArraySerializer`
* `JsonApiSerializer`

更多的信息可以查阅 [Fractal](http://fractal.thephpleague.com/transformers/) 和
[Laravel Fractal Wrapper](https://github.com/spatie/laravel-fractal)。

在需要返回 Json 数据格式 (`JsonApiSerializer`) 的情况下, 你可能需要查询一些 JSON 响应标准：

* [JSEND](https://labs.omniti.com/labs/jsend) (非常基础)
* [JSON API](http://jsonapi.org/format/) (非常流行，并且文档详尽)
* [HAL](http://stateless.co/hal_specification.html) (对于超文本来说非常有用，例如图像、视频、音频等)

<a name="Resource-Keys"></a>
### 资源密钥

#### 对于 JsonApiSerializer 来说。

转换器（transformer）允许添加一个 `ResourceKey` 来转换资源文件。你可以用一下两种方式在你的响应（Response）内容中添加 `ResourceKey`：

1. 通过调用 `$this->transform()` 方法各自的参数来手动的设置。注意，这只能设置 `top level` 的资源密钥，并且对 `included` 中的资源无效！
2. 通过在各自的 `Model` 文件中重载 `$resourceKey` 变量来指定资源密钥, (`protected $resourceKey = 'FooBar';`)。
如果 `Model` 文件中没有定义 `$resourceKey`, 将使用 `ShortClassName` 作为资源密钥。
例如 `App\Containers\User\Models\User::class` 的 `ShortClassName` 是 `User`。

#### 对于 DataArraySerializer 来说。

默认情况下， `object` 字段将被用作每次响应（Response）的资源密钥, 可以在每一个转换器（transformer）中手动设置，
*以后将全自动化*.

<a name="Error-Res-Format"></a>
### 错误响应（Response）格式

请求任意一个功能，例如认证功能，你将看到一个未授权响应是长什么样的。对于校验等功能来说也是一样。

<a name="build-res-from-con"></a>
## 在控制器（Controller）中构建一个响应（Response）：

请查看 [控制器响应工具函数]({{ site.baseurl }}{% link _docs/components/controllers.md %}) 章节。
