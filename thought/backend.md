# 后端开发规范和实践

本文档规定了技术团队**后端**开发规范和实践

## 语言

在这个 team 中,我们使用**python**, 除特殊的开发需要(需要相关负责人评估,批准)或 team 负责人提出转型, 否则**python**都将是后端最主要开发语言.

[python](https://www.python.org/)

## web framework

我们使用 tornado 和 turbo 来实现各种 web 服务

### [tornado](https://github.com/tornadoweb/tornado)

- [doc](http://tornado.readthedocs.org/en/stable/)
- [github](https://github.com/tornadoweb/tornado)

tornado 是后端开发唯一的 web framework, 除特殊的开发需要(需要相关负责人评估,批准)或 team 负责人提出转型,
否则**tornado** 都将是后端唯一的 web framework.


#### tornado 学习资料

- [wiki](https://github.com/tornadoweb/tornado/wiki/Links)
- [gist](http://tornadogists.com/)


#### 关于 tornado 必须要掌握的

- 理解基本的路由,handler处理,模板渲染,cookie处理
- 理解单线程运转
- 理解event loop机制

### [turbo](http://app-turbo.readthedocs.org/zh_CN/latest/)

- [doc](http://app-turbo.readthedocs.org/zh_CN/latest/)
- [github](https://github.com/wecatch/app-turbo)

turbo 是构建在 tornado 之上用以快速构建 web 服务的工具, turbo 提供了标准化的 web 服务结构和目录,并具有一下特性

- session
- 快速构建 RESTful api
- 方便扩展和移植

1.创建 project

```

turbo-admin startproject hello

```

此命令将创建一个project, 包含 turbo 项目最基本的目录结构和一个 app-server.
一个app-server是可运行的最小 web 单元, 一个 app-server 可以是 RESTFul api service 或 一个站点.

2.创建 app-server

```

cd hello

turbo-admin startserver god-server

```

此命令将创建一个 app-server, 名字是god-server, 进入god-server, 运行 python main.py 启动服务


3.创建子 app

```

cd god-server

turbo-admin startapp admin

```

此命令在 god-server 的 apps 目录下面创建了一个子 app:admin, 在 apps.settings 中加入 admin 就可以安装了.




## 基础工具库的编写原则

基础工具库是为了提供常用基础功能的代码库,必须满足以下要求才能在 team 中使用,推广

- 可独立安装
- 有完善的说明文档,文档包含
    - 如何安装
    - 如何使用
    - api 列表
    - 注意事项
    - 性能指标
    - 依赖关系
- 具备单元测试(功能性测试以及逻辑分支测试),覆盖率要达90%以上
- 要有相应的 bug 管理机制, 推荐使用 github issues
