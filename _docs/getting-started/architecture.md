---
title: "软件架构模式"
category: "开始"
order: 6
---

- [介绍](#intro)
- [Porto](#porto-intro)
  * [介绍](#introduction-1)
  * [Container 层](#container-layer)
    + [移除一个 Container (默认 container)](#rm-container)
    + [创建一个新 Container](#new-Containter)
      * [方法 1) 使用代码生成器](#use-Generator)
      * [方法 2) 手动](#manual-new-container)
    + [Container 约定](#Containter-Conventions)
  * [Ship 层](#ship-layer)
- [MVC](#mvc-intro)
  * [MVC 介绍](#mvc-introduction)
    + [标准 MVC 和 Apiato's MVC 之间的区别](#Difference-mvc)
    + [配置我的 Apiato MVC 应用](#Setup-mvc)
      - [1) 首先获取一个最新版的 Apiato](#1--first-get-a-fresh-version-of-apiato)
      - [2) 创建应用](#2--create-the--application-)
      - [3) 创建路由（Route）文件](#3--create-route-file)
      - [4) 创建控制器（Controller）](#4--create-controller)
      - [5) 创建模型（Models）](#5--create-models)
      - [6) 创建视图（Views）](#6--create-views)
      - [7) 创建转换器（Transformers）](#7--create-transformers)
      - [8) 创建 Service Providers](#8--create-service-providers)
      - [9) 创建数据库表迁移（Migrations）文件](#9--create-migrations)
      - [10) 创建数据填充（Seeds）](#10--create-seeds)
      - [更多 Classes](#more-classes)
    + [如何使用 Apiato 功能](#Apiato-features)

<a name="intro"></a>
### 介绍

在 Apiato 中构建项目时，两种最通用的软件架构：

- **Porto** (Route Request Controller Action Task Model Transformer).
- **MVC** (Model View Controller). *Apiato 的 MVC 和标准的 MVC 有一点小小的区别*

Porto 是 Apiato 推荐的用于设计可扩展的 API 架构方案。同时, Apiato 也支持采用流行的 MVC 架构（有一些小改动）来构建 API。

*Apiato 功能是使用 Porto 架构编写的, 也可以被用在任何其他架构中。*

接下来，你将了解如何使用这两种架构模式来设计你的项目。

## Porto

<a name="porto-intro"></a>
### 介绍

Porto 是一种包含 2 层结构的架构设计，分别是： **Containers** 层和 **Ship** 层。

**Container** 层包含了你处理应用业务逻辑的代码。有些类似模型化架构、模型驱动设计（DDD）和分层架构的思想；
Apiato 允许把业务逻辑拆分到多个不同的文件夹中，并把这些文件夹被称之为 **Containers**。你可以在所有 **Containers** 中共享你的代码。
另外，在 **Ship** 层实现基础功能性的代码，实现之后就基本不需要再去动的那种。

Apiato 的功能是采用 Porto 软件架构模式来开发实现的。这意味着 Apiato 的功能其实都放在 Container 中。

在你开始之前，花费 15 分钟先阅读 [Porto 原文文档](https://github.com/Mahmoudz/Porto) / [Porto 中文文档](https://learnku.com/articles/5338/porto-advanced-software-architecture-model) 是个明智的选择。

<a name="container-layer"></a>
### Container 层

你可以在 [这里（原版）](https://github.com/Mahmoudz/Porto#Containers-Layer) 或 [这里（中文版）](https://learnku.com/articles/5338/porto-advanced-software-architecture-model#Containers-Layer) 了解 Container 层的信息。

<a name="rm-container"></a>
#### 移除一个 Container (默认容器)

Apiato 包含了一些默认的 containers。虽然所有的 containers 都是可选的，但其中的一些包含了基础的功能。

如果你不想要 Apiato 内置的文档生成器功能。你可以简单的通过删除 `documentation` container 来去除相关功能。

要删除一个 Container，只需要简单的删除对应的文件夹，然后执行 `composer update` 来移除相关依赖。

<a name="new-Containter"></a>
#### 创建一个新 Container

<a name="use-Generator"></a>
**方法 1) 使用代码生成器：**

`php artisan apiato:container`

点击 [代码生成器]({{ site.baseurl }}{% link _docs/features/code-generator.md %}) 页面了解更多信息。

<a name="manual-new-container"></a>
**Option 2) 手动：**

1. 在 Containers 文件夹中创建一个文件夹。
2. 开始编写组件，并放在文件夹里。

*(Ship 引擎会帮你自动加载并注册所有 Container)*.

为了让自动加载顺畅运行，你必须遵守组件和目录命名约定。所以，当你创建组件时，你最好仔细了解一下组件的 `documentation page`。

<a name="Containter-Conventions"></a>
#### Container 约定

- Containers 名称应该首字母大写，并且采用驼峰命名法。
- Namespace 应该和 container 名称一致, (如果 container 名称是 "Printer"，那它的 namespace 应该是
`App\Containers\Printer`)。
- 虽然 Container 可能会被起任何名称。但是一个好的经验是建议用它最重要的 Model 名称来命名它。
*例如： 如果用户的线路是：（用户可以创建商店，商店包含商品），你应当创建 3 个 container，分别是 User、Store 和 Item。*

<a name="ship-layer"></a>
###  Ship 层

阅读 **[这里（原版）](https://github.com/Mahmoudz/Porto#Port-Layer)** 或 **[这里（中文版）](https://learnku.com/articles/5338/porto-advanced-software-architecture-model#Ship-Layer)** 来了解更多。

## MVC

<a name="mvc-intro"></a>
### MVC 介绍

由于 MVC 的流行，导致很多的开发人员没有足够的时间来学习了解其他新的架构。
所以 Apiato 也提供了一种 MVC 架构。 其中大概 97% 和 laravel 的 MVC 是一致的。

下面，你将了解如和利用你先前的 Laravel MVC 的知识来基于 Apiato 构建你的 API 应用。 

<a name="Difference-mvc"></a>
#### D标准 MVC 和 Apiato's MVC 之间的区别

Porto 架构并没有取代 MVC 架构, 而是更好的扩展了它。所以 Models, Views, Routes 和 Controllers 全部都继续存在，
但是不同的地方在于每个 `class type` 部分之间存在严格的职责划分。

<a name="Setup-mvc"></a>
#### 配置我的 Apiato MVC 应用

##### 1) 首先获取一个最新版的 Apiato

##### 2) 创建应用

如果你打开 `app/Containers/` 文件夹，你会看到一系列 Proto 的 Container。每一个 container 都提供了一些功能。
无论你是使用 Porto 还是 MVC 架构，你都不需要修改它们，所以你现在可以把这个文件夹忘了。

现在我们需要新建一个 `Application` 文件夹（这里放着你的 MVC 应用，用于替代 Laravel 项目根目录下的 `app` 文件夹）。
这个文件夹将包含你全部的 Model、View、Route、Controller 等文件。

##### 3) 创建路由（Route）文件

在 Laravel 中，路由文件是放在项目根目录下的 `routes/` 文件夹中。但是在 Apiato 的 MVC 架构中，路由文件应该在：

- `app/Containers/Application/UI/API/Routes/` (API 路由)
- `app/Containers/Application/UI/WEB/Routes/` (网页 路由)

新建 `app/Containers/Application/UI/API/Routes/api.php` 文件来替代 Laravel 本身的 `routes/api.php`
新建 `app/Containers/Application/UI/API/Routes/web.php` 文件来替代 Laravel 本身的 `routes/web.php`

在这两个文件中你可以像在 Laravel 中一样来创建你的访问点（Endpoint）。

> 注意: 在路由文件中，你必须使用 `$router->` 而不是 facade 的 `Route::` 方法。

Example:

```php
<?php

// 使用 `$router` 变量
$router->get('/', function () {
    return view('welcome');
});

// 不要用 `Route` facade
Route::get('/', function () {
    return view('welcome');
});
```

##### 4) 创建控制器（Controller）

在 Laravel 中，Controllers 文件放在 `app/Http/Controllers/` 文件夹中，但是在 Apiato 的 MVC 架构下，`Controller` 文件应该放在：

- `app/Containers/Application/UI/API/Controllers/Controller.php` (来处理 API 路由) 必须继承 `App\Ship\Parents\Controllers\ApiController`
- `app/Containers/Application/UI/WEB/Controllers/Controller.php` (来处理 WEB 路由) 必须继承 `App\Ship\Parents\Controllers\WebController`

##### 5) 创建模型（Models）

在 Laravel 中, 模型文件放在根目录的 `app/` 文件夹中。但是在 Apiato 的 MVC 架构下，模型文件应该放在 `app/Containers/Application/Models`。

所有的模型文件都必须继承（ `extend`） `App\Ship\Parents\Models\Model`。

> 注意： 为了保证所有的功能正常运行，模型 `User` 应该放在用户的 Container 中 (`app/Containers/User/Models/User.php`)。

##### 6) 创建视图（Views）

在 Laravel 中，视图文件被放在 `resources/views/` 文件夹下，而在 Apiato 的 MVC 架构中，视图文件应该还是放在那个目录或者放在 container 的 `app/Containers/Application/UI/WEB/Views/` 文件夹中。

##### 7) 创建转换器（Transformers

在 Laravel 中，转换器文件放在 `app/Transformers/` 文件夹下。但是在 Apiato 的 MVC 架构中，这些文件应该放在 `app/Containers/Application/UI/API/Transformers/` 中。

转换器文件必须继承 `App\Ship\Parents\Transformers\Transformer`。

##### 8) 创建 Service Providers

在 Laravel 中，服务提供者文件会放在 `app/Providers/` 文件夹下，但是在 Apiato 的 MVC 架构中，这些文件可以放在 `app/Containers/Application/Providers/` 文件夹下, 当然也可以放在任何其他位置。

如果你希望你的 Service Providers 能够被自动加载（不需要手动在 `config/app.php` 文件中注册）的话， 把你的文件 `MainServiceProvider.php` 移动到 `app/Containers/Application/Providers/MainServiceProvider.php`。如果你不需要自动加载的话，可以把文件放在任何位置，然后在 Laravel 中手动注册他们。

##### 9) 创建数据库表迁移（Migrations）文件

在 Laravel 中，数据库表迁移文件放在项目根目录的 `database/migrations/` 文件夹下。 而在 Apiato 的 MVC 架构中，它们可以继续放在相同的位置，或者放在 container 的 `app/Containers/Application/Data/Migrations/` 文件夹中。

##### 10) 创建数据填充（Seeds）

在 Laravel 中，数据填充文件放在项目根目录的 `database/migrations/` 文件夹下。而在 Apiato 的 MVC 架构中，他们可以继续放在相同的位置，或者放在 container 的 `app/Containers/Application/Data/Seeders/` 文件夹中。

##### 更多 Classes

所有其他类型的文件也是一样，你可以在文档查看它们被建议放在哪里，应该继承哪些父类，更多的信息可以在 **Slack** 和我们联系。

<a name="Apiato-features"></a>
#### 如何使用 Apiato 功能

Apiato 的功能都将以执行动作（Actions）和 任务（Tasks）的形式来提供。

- 每个执行动作（Action）的 class 仅包含一个单独的方法 `run`，并且这个方法也只实现一种功能。
- 每个任务（Task）的 class 仅包含一个方法 `run`，并且这个方法也只做一件小事(一小部分独立的业务逻辑功能)。

你可以用任何你喜欢的方式来使用 Actions/Tasks classes ：

- 通过 Apiato 的调用方式来使用 Apiato Facade `$user = \Apiato::call('Car@GetDriversAction', [$request->id]);`
- 使用带有全类名称的 Apiato Facade `$user = \Apiato::call(GetDriversAction::class, [$request->id]);`
- 使用具有完整类名的辅助调用函数 `$user = $this->call(GetDriversAction::class, [$request->id]);`
- 使用 Apiato 的调用方式的辅助函数来调用功能 `$user = $this->call('Car@GetDriversAction', [$request->id]);`
- 不需要 Apiato，直接使用原生 PHP `$user = $action = new GetDriversAction::class; $action->run($request->id);`
- 不需要 Apiato，直接使用原生 Laravel IoC `$user = \App::make(GetDriversAction::class)->run($request->id);`

随意点，说到底，这就是只拥有一个函数的类而已。
