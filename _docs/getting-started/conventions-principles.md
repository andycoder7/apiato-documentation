---
title: "原则与约定"
category: "开始"
order: 7
---

* [RESTful 风格的 HTTP 方法](#HTTP-Methods)
* [路由（Route）和执行动作（Action）的命名约定](#Naming-Conventions)
* [RESTful 风格的 URL 规范说明](#General-guidelines)
* [好的 URL 案例](#Good-examples)
* [关于 HTTP 方法的一些原则说明](#General-principles)

<a name="HTTP-Methods"></a>
### RESTful 风格的 HTTP 方法
- GET (查询): 从服务器检索一个特定的资源，或者该资源的集合。
- POST (新增): 在服务器上新增一个资源。
- PUT (更新): 更新服务器上某一个资源的全部属性（需要提供全部属性，哪怕该属性没有变动）。
- PATCH (更新): 更新服务器上某一项资源的部分属性（只提供修改的属性）。
- DELETE (删除): 从服务器上移除某一个资源。

<a name="Naming-Conventions"></a>
### 路由（Route）和执行动作（Action）的命名约定

- **GetAllResource**: 获取全部资源，你可以通过 `?search` 参数来筛选数据。
- **FindResourceByID**: 通过唯一主键来搜索一个资源。
- **CreateResource**: 创建一个资源
- **UpdateResource**: 更新现有的资源。
- **DeleteResource**: 删除一个资源。

<a name="General-guidelines"></a>
### RESTful 风格的 URL 规范说明

- 一个 URL 定义一个资源。
- URL 应当只包含名词，不包含动词。
- 应当统一使用名词的复数形式。
- 使用 HTTP 的方法 (GET, POST, PUT, DELETE) 来操作集合和元素。
- 不建议资源放的比这（resource/identifier/resource）还深。
- 版本信息应该放在 URL 的起始位置，例如： `http://apiato.test/v1/path/to/resource`.
- 如果传入的数据会改变访问点的逻辑，那么它应该放在 URL 中，如果不行，那就放在 header 中，例如 Auth Token。
- 不要使用请求参数来改变状态。
- 不建议 URL 路径混合大小写，全小写是最好不过的。
- 不要在你的 URI 中使用特定的扩展名，例如（.php, .py, .pl, 等）。
- 组织好你的 URI，保持路径简短清晰。
- 不要把元数据放在响应的 body 里，它应该被放在 header 中。

<a name="Good-examples"></a>
### 好的 URL 案例

- 通过唯一编码来获取某一辆车的信息：
	- `GET http://www.api.apiato.test/v1/cars/123`
- 获取全部车辆信息：
	- `GET http://www.api.apiato.test/v1/cars`
- 通过一个或多个条件来搜索车辆信息：
	- `GET http://www.api.apiato.test/v1/cars?search=maker:mercedes`
	- `GET http://www.api.apiato.test/v1/cars?search=maker:mercedes;color:white`
- 需要有序的结果队列：
	- `GET http://www.api.apiato.test/v1/cars?orderBy=created_at&sortedBy=desc`
	- `GET http://www.api.apiato.test/v1/cars?search=maker:mercedes&orderBy=created_at&sortedBy=desc`
- 获取车辆的指定属性信息：
	- `GET http://www.api.apiato.test/v1/cars?filter=id;name;status`
	- `GET http://www.api.apiato.test/v1/cars/123?filter=id;name;status`
- 获取这辆车的全部驾驶员：
	- `GET http://www.api.apiato.test/v1/cars/123/drivers`
	- `GET http://www.api.apiato.test/v1/cars/123/drivers/123/addresses`
- 在车辆信息的返回的时候带上该车辆的其他关联主体：
	- `GET http://www.api.apiato.test/v1/cars/123?include=drivers`
	- `GET http://www.api.apiato.test/v1/cars/123?include=drivers,owner`
- 新增一部车辆信息
	- `POST http://www.api.apiato.test/v1/cars`
- 为一辆车新增驾驶员信息
	- `POST http://www.api.apiato.test/v1/cars/123/drivers`

<a name="General-principles"></a>
### 关于 HTTP 方法的一些原则说明

- 为了防止 Google 的爬虫不小心修改你的数据，不要用 GET 方法来改变数据。其他情况尽可能使用 GET 方法。
- 除非你要更新整个资源信息或者可以合理的对这个 URI 使用 GET 方法，否则不要用 PUT 方法。
- 不要使用 POST 方法来获取长期不变的数据，因为它有可能会被缓存。
- 不要用 PUT 方法去执行一个不幂等的操作。
- 如果你的数据量很大用 POST，正常情况下请用 GET 方法来获取一些例如计算结果之类的数据。
- 如果有疑惑的话，那就采用 POST 而不是 PUT 方法。
- 无论何时，如果你要做一些像是 RPC 的操作，那就请使用 POST 方法。
- 对于分级的资源，请使用 PUT 方法来操作各级的资源
- 一般使用 DELETE 而不是 POST 方法来删除资源。
