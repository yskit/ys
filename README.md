# Ys.js 是什么?

**[YS](https://github.com/yskit/ys) 为企业级框架和应用而生**，它是一套基于[nodejs](https://nodejs.org)的渐进式开发应用架构。我们希望由 YS 孕育出更多上层框架，帮助开发团队和开发人员降低开发和维护成本。

# 设计原则

我们深知企业级应用在追求规范和共建的同时，还需要考虑如何平衡不同团队之间的差异，求同存异。所以我们没有选择社区常见框架的大集市模式（集成如数据库、模板引擎、前端框架等功能），而是专注于提供 Web 开发的核心功能和一套灵活可扩展的插件机制。我们不会做出技术选型，因为固定的技术选型会使框架的扩展性变差，无法满足各种定制需求。通过 YS，团队的架构师和技术负责人可以非常容易地基于自身的技术架构在 YS 基础上扩展出适合自身业务场景的框架。

YS 的插件机制有很高的可扩展性，一个插件只做一件事（比如 MySQL 数据库封装成了 [ys-pg-dbo](https://github.com/yskit/ys-pg-dbo)）。YS 通过框架聚合这些插件，并根据自己的业务场景定制配置，这样应用的开发成本就变得很低。

YS 奉行『约定优于配置』，按照一套统一的约定进行应用开发，团队内部采用这种方式可以减少开发人员的学习成本，开发人员不再是『钉子』，可以流动起来。没有约定的团队，沟通成本是非常高的，比如有人会按目录分栈而其他人按目录分功能，开发者认知不一致很容易犯错。但约定不等于扩展性差，相反 YS 有很高的扩展性，可以按照团队的约定定制框架。使用 [Loader](https://github.com/yskit/ys-loader) 可以让框架根据不同环境定义默认配置，还可以覆盖 YS 的默认约定。

# 与社区框架的差异

[Express](https://expressjs.com/) 是 Node.js 社区广泛使用的框架，简单且扩展性强，非常适合做个人项目。但框架本身缺少约定，标准的 MVC 模型会有各种千奇百怪的写法。YS 按照约定进行开发，奉行『约定优于配置』，团队协作成本低。

[Sails](https://sailsjs.com/) 是和 YS 一样奉行『约定优于配置』的框架，扩展性也非常好。但是相比 YS，Sails 支持 Blueprint REST API、[WaterLine](https://github.com/balderdashy/waterline) 这样可扩展的 ORM、前端集成、WebSocket 等，但这些功能都是由 Sails 提供的。

[Egg.js](https://github.com/eggjs/egg) 与 YS 的设计理念基本相同，不同的时候，YS解决了Egg.js所没有的生命周期问题，同时可以通过[ys-pg-dbo](https://github.com/yskit/ys-pg-dbo)插件进行内部线程的事物回滚、物理回滚和API回滚等。YS在设计上，特别是在AGENT层的架构，独树一帜，我们约定了一种进程之间的`微服务协议`通讯模式，比如`agent://test-service/api/user/19222`规范来获取进程处理后的数据。还有一点与Egg.js不同的是，在插件的设计上，我们对Agent层的规范扩展更加到位。

# 特性

- 提供基于 YS 定制上层框架的能力
- 高度可扩展的插件机制
- 内置多进程管理
- 基于多引擎协议开发，性能优异（KOA、MICRO）
- 框架稳定，测试覆盖率高
- 渐进式开发

# 宏观体验

YS在整体设计上，都表现出了非常优异的开发性能。

## 脚手架工具

为了提升开发效率，使开发者能够在最快的时间内生成文件模板，我们提供了一整套脚手架[ys-cli](https://github.com/yskit/ys-cli)，用来快速创建项目、插件以及快速生成各模块代码的一个工具。它还支持插件的命令行功能，插件能够为其扩展快速开发功能或者其他功能。

## 插件

- [ys-pg-dbo](https://github.com/yskit/ys-pg-dbo) 数据引擎插件 支持回滚操作
- [ys-pg-micro-router](https://github.com/yskit/ys-pg-micro-router) 微服务路由插件
- [ys-pg-dbo-cache](https://github.com/yskit/ys-pg-dbo-cache) 数据缓存插件
- **[ys-pg-koa-router](https://github.com/yskit/ys-pg-koa-router)** Koa路由插件
- [ys-pg-koa-smart-router](https://github.com/yskit/ys-pg-koa-smart-router) Koa轻量路由插件

## 服务

- [ys-fw-koa](https://github.com/yskit/ys-fw-koa) Koa服务
- [ys-fw-micro](https://github.com/yskit/ys-fw-micro) 微服务

# 安装

```shell
npm i ys-cli -g
ys new my-project
cd my-project
npm run dev
open http://localhost:8080
```

# License

[MIT](https://github.com/yskit/ys/blob/master/LICENSE)