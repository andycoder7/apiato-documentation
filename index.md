---
title: "欢迎使用 Apiato"
---

> **借助 PHP 7.4 和 laravel 6 帮你更快的构建应用接口.**

![apiato.jpg]({{ site.baseurl }}/images/image-rounded.png)

[![apiato](https://img.shields.io/badge/Status-Awesome-brightgreen.svg)](https://github.com/apiato/apiato)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/apiato/apiato/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/apiato/apiato/?branch=master)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/ce8fed7f8fcd492ebbe5ef0fb36c0a9a)](https://www.codacy.com/app/mahmoudz/apiato?utm_source=github.com&utm_medium=referral&utm_content=apiato/apiato&utm_campaign=badger)
[![Build Status](https://scrutinizer-ci.com/g/apiato/apiato/badges/build.png?b=master)](https://scrutinizer-ci.com/g/apiato/apiato/build-status/master)
[![Build Status](https://travis-ci.org/apiato/apiato.svg?branch=master)](https://travis-ci.org/apiato/apiato)
[![Latest Stable Version](https://poser.pugx.org/apiato/apiato/v/stable)](https://packagist.org/packages/apiato/apiato)
[![Backers on Open Collective](https://opencollective.com/apiato/backers/badge.svg)](#backers)
[![Sponsors on Open Collective](https://opencollective.com/apiato/sponsors/badge.svg)](#sponsors)
[![License](https://poser.pugx.org/apiato/apiato/license)](https://packagist.org/packages/apiato/apiato)


## Apiato 是什么

<!-- **Apiato** is a framework for building scalable and testable API-Centric Applications with PHP, build on top of Laravel. -->
**Apiato** 是一个基于 PHP 和 Laravel 的框架，它可以帮助我们方便的构建一个可扩展、易测试的、以 API 为中心的应用。
<!-- It is designed to help you build scalable API's faster, by providing tools and functionalities that facilitates the development of any API-Centric App. -->
我们可以用它提供的基础工具和组件来更快的编写 API。
<!-- Apiato uses the best frameworks, tools and conventions in a very creative way, to deliver a rich set of features for a modern PHP Application. -->
Apiato 把最棒的框架、工具和开发习惯奇妙的组合在了一起，并提供一系列丰富的功能集合，来帮助我们构建一个现代化的 PHP 应用。
<!-- **Why!?** Because setting up a solid API from scratch is time consuming (and of course, time is money!).
Apiato gives you the core features of robust API's fully documented, for free; so you can focus on writing your business logic, thus deliver faster to your clients. -->
**为什么！？** 因为构建 API 是项目的时间消耗大户（没错，时间就是金钱！）。而构建一个健壮且自动文档化的API程序所需的核心功能 Apiato 都可以提供，然后，我们就可以专注于编写我们的业务逻辑代码，来帮助我们更快的向客户提供服务。

### 功能

<!-- Apiato comes with an amazing list of features. -->
Apiato 提供了以下一系列惊人的功能：

![]({{ site.baseurl }}/images/features.png)

## 软件架构

**Apiato** 使用了新的软件架构模式 **[Porto](https://github.com/Mahmoudz/Porto)** 来构建。

<!-- **Porto 软件架构模式（SAP）** is a modern Software Architectural Pattern, designed to help developers organize their Code in a super maintainable way. It is very helpful for big and long term projects, as they tend to have higher complexity with time. -->
**Porto 软件架构模式（SAP）** 是一个现代的软件架构模式，这个模式被设计用于帮助开发者以一种超级可维护的方式来组织他们的代码。这对于越来越复杂的大型或者长期项目来说是非常有用的，
<!-- It's completely **optional** to build your application using the Porto architecture.
Alternatively, you can build it using the [MVC]({{ site.baseurl }}{% link _docs/getting-started/architecture.md %}) architecture, and still benefit from all the features of Apiato. -->
通过使用 Porto 架构，你可以把你的项目设计成完全 **模块化**。或者，你也可以继续使用 [MVC]({{ site.baseurl }}{% link _docs/getting-started/architecture.md %}) 的模式来设计你的项目。它同样也可以享受到 Apiato 提供的各种功能。

### 如何来阅读本文档

本文档工包含 4 个章节：
<!-- The documentation has 4 sections: -->

<!-- - **Getting Started**: contains mainly the project installation steps.
- **General**: contains few general things to get you started.
- **Features**: explains how to use each feature of Apiato, and show how it works and how it can be configured to meet your needs.
- **Components**: explains how, where and why you need to use each component "class". In each component page you will see:
  * **Definition**: what is the the component and what it's role.
  * **Principles**: the general principles of the component, which could be applied to any programming language.
  * **Rules**: how to apply the component principles in Apiato (a PHP/Laravel project), to ensure a smooth operation.
  * **Folder Structure**: the folder structure, that shows where to place your component.
  * **Code Sample**: a boilerplate to show how to write and use the component.
  * **Misc**: things related to the component, like configurations and other stuff you might need while coding. -->

- **开始**: 包含项目安装的主要步骤.
- **概述**: 包含一些概述性的内容来帮助你理解。
- **功能**: 介绍了 Apiato 各种功能的使用方法、实现原理，和可配置方案。
- **组件**: 介绍了为什么、在哪里和如何使用每一个组件类(class)，在每个组件小节中，你将看到：
  * **定义**: 这个组件是什么，它的职责又是什么。
  * **原则**: 这个组件的功能界定是什么，这是一个抽象的功能性描述，你可以用任何的编程语言来实现这个原则。
  * **规定**: 在 Apiato 架构（即 PHP/Laravel 项目中）中如何优雅的实现这个原则
  * **文件目录架构**: 文件目录架构是怎样的，你应该把你的组件放在哪里。
  * **示例代码**: 如何编写和使用这个组件的示例代码。
  * **其他**: 其他和这个组件相关内容，例如配置说明和其他一些你在编码时可能需要的功能说明。

### 惯例说明

<!-- > The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 [[RFC2119](http://tools.ietf.org/html/rfc2119)]. -->

> 本文中的关键词 “必须(MUST)”，“必须不(MUST NOT)”，“需要(REQUIRED)”，“应当(SHALL)”，“不应当(SHALL NOT)”，“应该(SHOULD)”，“不应该(SHOULD NOT)”，“建议(RECOMMENDED)”，“可能(MAY)”，‘可选的(OPTIONAL)’ 意思参见 RFC 2119 [[RFC2119](http://tools.ietf.org/html/rfc2119)]

<a name="Sponsors"></a>
##  Apiato 的赞助者们:

<a href="https://opencollective.com/apiato/sponsor/0/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/0/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/1/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/1/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/2/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/2/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/3/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/3/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/4/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/4/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/5/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/5/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/6/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/6/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/7/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/7/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/8/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/8/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/9/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/9/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/10/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/10/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/11/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/11/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/12/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/12/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/13/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/13/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/14/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/14/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/15/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/15/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/16/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/16/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/17/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/17/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/18/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/18/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/19/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/19/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/20/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/20/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/21/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/21/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/22/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/22/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/23/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/23/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/24/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/24/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/25/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/25/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/26/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/26/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/27/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/27/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/28/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/28/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/29/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/29/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/30/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/30/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/31/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/31/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/32/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/32/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/33/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/33/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/34/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/34/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/35/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/35/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/36/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/36/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/37/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/37/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/38/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/38/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/39/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/39/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/40/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/40/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/41/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/41/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/42/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/42/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/43/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/43/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/44/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/44/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/45/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/45/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/46/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/46/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/47/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/47/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/48/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/48/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/sponsor/49/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/sponsor/49/avatar.svg?requireActive=false"></a>

你可以通过这里来赞助 [organization](https://opencollective.com/apiato/contribute/) Apiato。
<br>
你的头像将显示在 [github repository](https://github.com/apiato/apiato/) 和 [documentation](http://apiato.io/) 的主页.
<br>
更多信息请联系 <a href = "mailto: support@apiato.io">support@apiato.io</a>.


<a name="Backers"></a>
## 支持者们

<a href="https://opencollective.com/apiato/backer/0/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/0/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/1/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/1/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/2/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/2/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/3/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/3/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/4/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/4/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/5/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/5/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/6/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/6/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/7/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/7/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/8/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/8/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/9/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/9/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/10/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/10/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/11/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/11/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/12/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/12/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/13/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/13/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/14/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/14/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/15/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/15/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/16/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/16/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/17/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/17/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/18/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/18/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/19/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/19/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/20/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/20/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/21/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/21/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/22/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/22/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/23/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/23/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/24/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/24/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/25/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/25/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/26/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/26/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/27/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/27/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/28/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/28/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/29/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/29/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/30/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/30/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/31/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/31/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/32/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/32/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/33/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/33/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/34/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/34/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/35/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/35/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/36/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/36/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/37/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/37/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/38/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/38/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/39/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/39/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/40/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/40/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/41/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/41/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/42/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/42/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/43/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/43/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/44/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/44/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/45/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/45/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/46/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/46/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/47/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/47/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/48/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/48/avatar.svg?requireActive=false"></a>
<a href="https://opencollective.com/apiato/backer/49/website?requireActive=false" target="_blank"><img src="https://opencollective.com/apiato/backer/49/avatar.svg?requireActive=false"></a>

<a name="Donations"></a>
### 经济支持

来帮助我们维持 Apiato 吧。

<b>方法 1:</b> 通过 [Paypal](https://paypal.me/mzmmzz) 捐款
<br>
<b>方法 2:</b> 成为 [Github Sponsors](https://github.com/sponsors/Mahmoudz) 的赞助者
<br>
<b>方法 3:</b> 成为 [Open Collective](https://opencollective.com/apiato/contribute) 的支持者


<a name="translator"></a>
### 来自翻译者的个人植入

来帮助我更新中文文档吧。

<b>方法 1:</b> 通过支付宝捐款：支付宝账号：18862237850，姓名：姚文强
<br>
<b>方法 2:</b> 通过微信捐款：微信 ID：Andy_at_working，昵称: andy


<a name="Getting started"></a>
## 开始

安装并享受吧 ：）[安装指南]({{ site.baseurl }}{% link _docs/getting-started/installation.md %})


<!--**LTS (Long-Term Support)** release is available. And offers support for 12 months, after the release date.-->
<!--The current LTS version is **7.2** (Release date 2017-11-11).-->
<!--It offers bug fixes (for 12 months) and security updates (for 12 months). And does not get any new features.-->

<a name="Chat"></a>
### 和我们联系

点击下面图标加入 [Slack](https://slackin-mezlsumyvc.now.sh/) 聊天室。

<a href="https://slackin-mezlsumyvc.now.sh/">
   <img src="https://s19.postimg.cc/h7pvzy9ar/Slack-i_OS-icon.png" alt="Apiato SLACK"/>
</a>


<a name="Testimonials"></a>
## 评价

> 了解一些 Apiato 用户对我们的评价： < **[feedbacks]({{ site.baseurl }}{% link _docs/miscellaneous/testimonials.md %})** >
