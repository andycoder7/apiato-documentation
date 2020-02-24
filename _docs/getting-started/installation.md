---
title: "安装"
category: "开始"
order: 2
---

* [A) Apiato 安装](#App)
	* [1) 脚本设置](#Code-Setup)
		* [方法 1: 通过 Composer 全自动](#App-Composer)
		* [方法 2: 通过 Git 手动安装](#App-Git)
	* [2) 数据库设置](#Setup-Database)
	* [3) OAuth 2.0 设置](#Prepare-OAuth)
	* [4) 文档设置](#Documentation)
	* [5) 测试设置](#Testing)
* [B) 开发环境配置](#Development-Environment)
	* [方法 1: 使用 Laradock 和 Docker](#Dev-Env-Opt-A)
	* [方法 2: 使用 Homestead 和 Vagrant](#Dev-Env-Opt-B)
	* [方法 3: 使用 MAMP/WAMP 或者其他](#Dev-Env-Opt-C)
* [C) 让我们嗨起来](#Play)


<a name="App"></a>
## A) Apiato 应用安装

**Apiato** 可以通过 Composer（推荐）来全自动安装，或者通过 Git / 手动下载 来自行安装：

<a name="Code-Setup"></a>
### 1) 脚本设置

<a name="App-Composer"></a>
#### 1.A) 通过 Composer 全自动时

1) 克隆代码仓库，安装依赖，然后配置：

方法 1: 最新的 [稳定版](https://github.com/apiato/apiato/releases/latest):

```shell
composer create-project apiato/apiato my-api
```

方法 2: 去 [开发](https://github.com/apiato/apiato/commits/master) 分支 "dev master" *(开发版)*:
*这会给你提供下一版才具备的功能。但是当版本更新时，你需要通过运行 `composer install` 来让你的项目和仓库的主分支保持同步。*

```shell
composer create-project apiato/apiato my-api dev-master
```

2) 根据你的系统环境来编辑 `.env` 中的变量（设置数据库、访问地址等……）.

3) 然后进行下面的 [2) 数据库设置](#Setup-Database).

<a name="App-Git"></a>
#### 1.B) 通过 Git 手动安装

你可以直接从代码仓库下载 `.ZIP` 文件或者通过 `Git` 来克隆代码仓库（推荐使用 Git）：

1) 使用 `Git` 来克隆代码仓库：

 ```shell
git clone https://github.com/apiato/apiato.git
 ```

> **提示** <br>
> 如果你在使用 [Laradock](http://laradock.io/)，你可以尝试运行下面的这些来自于 `workspace` 容器的命令. <br>
> 首先，你需要在 Laradock 的文件夹下通过运行 `docker-compose up -d nginx mysql php-fpm workspace redis` 来安装那些你需要的工具_（当然，你可以添加任何你需要的工具）_。<br>
> 然后，通过运行 `docker-compose exec workspace bash` 进入 `workspace` 容器。 <br>
> 更对信息可以查看之后的 **通过 Laradock 来使用 Docker** 章节。

2) 安装所有的依赖包 (包括容器所需的依赖):

```shell
composer install
```

3) 创建 `.env` 文件，然后把 `.env.example` 中的内容复制一份进去。

```shell
cp .env.example .env
```

*按照你的本地环境来配置所有的变量*

4) 生成随机密钥 `APP_KEY`

```shell
php artisan key:generate
```

5) 删除项目根目录中的 `.git` 文件夹，然后运行 `git init` 来初始化你自己的项目。

<a name="Setup-Database"></a>
### 2) 数据库配置

1) 数据库表结构迁移(Migrate):

运行数据库表结构迁移命令：

```shell
php artisan migrate
```

2) 运行命令来填充初始和测试数据：

```shell
php artisan db:seed
```

3) 可选的：默认情况下 Apiato 会填充一个 "超级用户", 并给它 `admin` 角色 (这个角色没有任何的权限限制)。

在任何时候，运行下面的命令，都可以给 `admin` 角色全部系统中默认填充的权限。

```
php artisan apiato:permissions:toRole admin
```

<a name="Prepare-OAuth"></a>
### 3) OAuth 2.0 设置

1) 创建加密密钥来生成安全的访问令牌，并创建 "个人权限" 和 "密码授权" 客户端，这两个客户端将被用于生成访问令牌：

```shell
php artisan passport:install
```

<a name="Documentation"></a>
### 4) 文档设置

如果你准备使用 ApiDoc JS，那么请执行以下设置，不准备的话你可以选择跳过：

1) 使用 NPM 或者你喜欢的依赖管理工具来安装 [ApiDocJs](http://apidocjs.com/)：

*你可以通过 `-g` 参数来全局安装，也可以不加 `-g` 参数来仅安装在项目本地*

```shell
npm install apidoc
```

如果你在项目根目录的 `package.json` 文件中确认包含了 ApiDoc JS，那么你只需要在项目根目录执行 `npm install` 就可以完成安装了。


2) 运行 `php artisan apiato:docs`

在 `apiato:docs` 之后，执行一个类似如下的命令：

```
apidoc -c app/Containers/Documentation/ApiDocJs/public -f public.php -i app -o public/api/documentation
```

##### 更多信息请查看 [API 文档生成器]({{ site.baseurl }}{% link _docs/features/api-docs-generator.md %})。

<a name="Testing"></a>
### 5) 测试配置

1) 打开 `phpunit.xml` 文件，检测确认其中的环境变量与你的域名相匹配。

2) 运行测试

```shell
vendor/bin/phpunit
```

<a name="Development-Environment"></a>
## B) 开发环境设置

你可以选择你喜欢的开发环境去运行 **Apiato** 。本文会讲解你如何在 
[Vagrant](https://www.vagrantup.com/) (通过 [Laravel Homestead](https://laravel.com/docs/master/homestead)) 或者
[Docker](https://www.docker.com/) (通过 [Laradock](https://github.com/Laradock/laradock))中运行 Apiato。

你可以选择其中一个，当然，你可以选择其他的方案，例如：
[Larvel Valet](https://laravel.com/docs/valet), [Laragon](https://laragon.org/) 或者直接在你本机运行。

> **注意!** <br>
> ICANN 已经官方支持 `.dev` 是一个通用顶级域名 (gTLD)。所以 **不** 再建议在本地开发环境配置中使用 `.dev` 域名！本文已经改用 `.test` 来取代 `.dev`。
> 当然，你也可以选择改用 `.example`, 或者 `.localhost` 或任何满足你实际情况的域名。 [了解更多](http://www.faqs.org/rfcs/rfc2606.html).

<a name="Dev-Env-Opt-A"></a>
### A.1) 使用 Docker (通过 Laradock)

**Laradock** 是一个包含 PHP 开发环境的 Docker，可以让我们非常方便在 Docker 中运行 PHP 应用。

1) 安装 [Laradock](https://github.com/LaraDock/laradock#installation).

2) 跳转到 `laradock` 文件夹:

```shell
cd laradock
```
这个文件夹包含一个 `docker-compose.yml` 文件。 (来自于 LaraDock 项目)。

2.1) 如果你没有这么做，把 `env-example` 文件拷贝并重命名为 `.env`。

```shell
cp env-example .env
```

3) 创建 docker 容器

```shell
docker-compose up -d nginx mysql redis beanstalkd
```

4) 确认你在 `.env` 文件中设置的 `Docker IP` 是 `DB` 和 `Redis` 的 `Host`。 

5) 给 Hosts 文件添加域名：

5.1) 在你本机打开 `/etc/hosts` 文件。

*我们将使用 `apiato.test` 作为本地域名 (你可以按照任何你的喜好随意修改)。*

5.2) 把域名及其子域名映射到本机 127.0.0.1:

```text
127.0.0.1  apiato.test
127.0.0.1  api.apiato.test
127.0.0.1  admin.apiato.test
```

如果你使用 NGINX 或者 Apache，请确保在你的系统配置文件中 **server_name** (NGINX 里的) 或者 **ServerName** (Apache 里的)被设置为
`apiato.test api.apiato.test admin.apiato.test`。
*(同样，不要忘了把 **Root** 或者 **DocumentRoot** 指向 apiato 中的 public 文件夹，即 `apiato/public`)*。

<a name="Dev-Env-Opt-B"></a>
### A.2) 使用 Vagrant (通过 Laravel Homestead)

1) 配置 Homestead：

1.1) 打开 Homestead 配置文件：

```shell
homestead edit
```

1.2) 把 `api.apiato.test` 域名映射到项目的 public 目录 - 例如：

```text
sites:
	- map: api.apiato.test
  	  to: /{full-path-to}/apiato/public
```

1.3) 你可以把其他其他域名像是： `apiato.test` 和 `admin.apiato.test` 映射到其他的网页应用：

```text
	- map: apiato.test
  	  to: /{full-path-to}/clients/web/user
	- map: admin.apiato.test
  	  to: /{full-path-to}/clients/web/admin
```

注意: 以上示例中的 `/{full-path-to}/clients/web/***` 是相互独立的不同的的应用。它们都拥有各自的代码仓库，在不同的文件夹中，但是都属于同一个 Apiato。
如果你的管理员、用户、或者其他类别的应用都基于 Apiato，那么你需要把它们都指向 Apiato 的项目文件夹 `/{full-path-to}/apiato/public`。
如果这样的话，你应该会有一个类似这样的配置：

```text
    - map: api.apiato.test
      to: /{full-path-to}/apiato/public
    - map: apiato.test
      to: /{full-path-to}/apiato/public
    - map: admin.apiato.test
      to: /{full-path-to}/apiato/public
```

2) 在 Hosts 文件中添加域名：

2.1) 在你本机打开 `/etc/hosts` 文件。

*我们将使用 `apiato.test` 作为本地域名 (你可以按照任何你的喜好随意修改)。*

2.2) 把域名及其子域名映射到 Vagrant 的 IP 地址：

```text
192.168.10.10   apiato.test
192.168.10.10   api.apiato.test
192.168.10.10   admin.apiato.test
```

如果你使用 NGINX 或者 Apache，请确保在你的系统配置文件中 **server_name** (NGINX 里的) 或者 **ServerName** (Apache 里的)被设置为
`apiato.test api.apiato.test admin.apiato.test`。
*(同样，不要忘了把 **Root** 或者 **DocumentRoot** 指向 apiato 中的 public 文件夹，即 `apiato/public`)*。

2.3) 运行虚拟机：

```shell
homestead up --provision
```

*如果你在访问子域名时看到 `No input file specified` !
请尝试执行 `homestead halt && homestead up --provision`。*

<a name="Dev-Env-Opt-C"></a>
### A.3) 使用其他方式

如果你不想在虚拟环境安装部署，你可以可以直接在你本机安装。请确认
[环境要求列表]({{ site.baseurl }}{% link _docs/getting-started/requirements.md %})都已满足。

<a name="Play"></a>
## C) 让我们嗨起来

现在你可以看到它了。

1.a. 打开你的浏览器，然后访问：

- `http://apiato.test` 你应该看到一个 `Apiato` 在正当中的网页。
- `http://admin.apiato.test` 你应该看到一个登录页面。

1.b. 打开你的 HTTP 客户端，然后发起请求：

- `http://api.apiato.test/` 你应该看到一个 JSON 格式的响应数据，内容是：`"Welcome to apiato."`,
- `http://api.apiato.test/v1` 你应该看到一个 JSON 格式的响应数据，内容是： `"Welcome to apiato (API V1)."`,

2) 向 API 发起 HTTP 请求：

*你可以使用 [Postman](https://www.getpostman.com/), [HTTPIE](https://github.com/jkbrzt/httpie) 或者
其他任何你喜欢的工具来发起 HTTP 请求*

让我们用 **cURL** 来测试 `http://api.apiato.test/v1/register` 接口 (用户注册) ：

```shell
curl -X POST -H "Accept: application/json" -H "Cache-Control: no-cache" -F "email=mahmoud@zalt.me" -F "password=so-secret" -F "name=Mahmoud Zalt" "http://api.apiato.test/v1/register"
```

你应该获得如下响应内容：

```json
Access-Control-Allow-Origin → ...
Cache-Control → ...
Connection → keep-alive
Content-Language → en
Content-Type → application/json
Date → Wed, 11 Apr 2000 22:55:88 GMT
Server → nginx
Transfer-Encoding → chunked
Vary → Origin
X-Powered-By → PHP/7.7.7
X-RateLimit-Limit → 30
X-RateLimit-Remaining → 29

{
  "data": {
    "object": "User",
    "id": 77,
    "name": "Mahmoud Zalt",
    "email": "apiato@mail.com",
    "confirmed": null,
    "nickname": "Mega",
    "gender": "male",
    "birth": null,
    "social_auth_provider": null,
    "social_id": null,
    "social_avatar": {
      "avatar": null,
      "original": null
    },
    "created_at": {
      "date": "2017-04-05 16:17:26.000000",
      "timezone_type": 3,
      "timezone": "UTC"
    },
    "updated_at": {
      "date": "2017-04-05 16:17:26.000000",
      "timezone_type": 3,
      "timezone": "UTC"
    },
    "roles": {
      "data": []
    }
  }
}
```
