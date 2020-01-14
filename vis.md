


> Written with [StackEdit](https://stackedit.io/).
# 后台数据可视化平台

<p align="center">
  <a href="https://github.com/vuejs/vue">
    <img src="https://img.shields.io/badge/Python-2.6.10-brightgreen.svg" alt="vue">
  </a>
  <a href="https://github.com/PanJiaChen/vue-element-admin/releases">
    <img src="https://img.shields.io/github/release/PanJiaChen/vue-element-admin.svg" alt="GitHub release">
  </a>
  <a href="https://gitter.im/vue-element-admin/discuss">
    <img src="https://badges.gitter.im/Join%20Chat.svg" alt="gitter">
  </a>
</p>

## 简介

基于 [superset](https://github.com/apache/incubator-superset) 实现后台数据分析平台。它使用了最新的BI技术栈，基于Python、Flask、D3、Pandas、SqlAlchemy，权限验证，提炼了典型的业务模型，提供了丰富的功能组件，它可以帮助你快速搭建企业级中数据库产品原型。

## 配置环境

你需要在本地安装 [docker](http://nodejs.org/) 和 [git](https://git-scm.com/)。本项目技术栈基于 [ES2015+](http://es6.ruanyifeng.com/)、[vue](https://cn.vuejs.org/index.html)、[vuex](https://vuex.vuejs.org/zh-cn/)、[vue-router](https://router.vuejs.org/zh-cn/) 、[vue-cli](https://github.com/vuejs/vue-cli) 、[axios](https://github.com/axios/axios) 和 [element-ui](https://github.com/ElemeFE/element)

使用docker-compose安装，支持SQLLite/PG/MySQL方式的元数据存储
```bash
 1. 第三方镜像
    docker pull amancevice/superset
 3. 创建本地目录
	mkdir /opt/docker/superset/ -p
 4. 创建映射端口
	docker run -d -p 8087:8088 -v /opt/docker/superset:/home/superset amancevice/superset
 5. 查看镜像ID
	docker ps
 6. 设置管理员用户名和密码
	docker exec -it <容器ID> fabmanager create-admin --app superset
 7. 初始化数据库
 　 docker exec -it <容器ID> superset db upgrade
 8. superset初始化
 　 docker exec -it <容器ID> superset init
 9. 运行superset服务
	docker exec -it <容器ID> superset runserver
```
更改密码
fabmanager reset-password --app superset --username <用户名> --password <密码>

数据库详细配置
[https://docs.sqlalchemy.org/en/13/core/engines.html#database-urls](https://docs.sqlalchemy.org/en/13/core/engines.html#database-urls)
## 功能
```
- 多环境发布
  - dev sit stage prod

- 全局功能
  - 动态侧边栏（支持多级路由嵌套）
  - 动态面包屑
  - Svg Sprite 图标
  - Screenfull全屏
  - 自适应收缩侧边栏
```
## 项目结构

## 界面
用户名: admin
密码: admin
```vue

├── views                      # 界面目录
│   │── notifi-manage          # 一键通知管理
│       │── apply              # 申请列表
│       │── group              # 群列表
│           │── components     # 组件
│               │── GroupAdd   # 添加群界面
│               │── GroupInfo  # 修改群界面
│   │── error-page             # 错误界面
│   │── icons                  # 图标管理
│   │── login                  # 登录界面
└── router                     # 界面路由配置

```
## 开发

```bash
[原文链接](https://zhuanlan.zhihu.com/p/28485468)

创建
superset run -p 8088 --with-threads --reload --debugger

# 克隆项目
git clone https://git.dev.tencent.com/PHPcoding/elementui-admin.git

# 进入项目目录
cd elementui-admin

# 安装依赖
npm install

# 如果node-sass安装失败使用指定源安装
npm i node-sass --sass_binary_site=https://npm.taobao.org/mirrors/node-sass

# 建议不要直接使用 cnpm 安装以来，会有各种诡异的 bug。可以通过如下操作解决 npm 下载速度慢的问题
npm install --registry=https://registry.npm.taobao.org

# 启动服务
npm run dev
```

浏览器访问 http://localhost:1990


## 配置 接口地址
.env.development 配置测试环境地址

.env.production 配置生成环境地址

Url目录配置
vue.config.js
 ```js
 publicPath: '/zt/web/ysrc/2019/06/group',
````

## 发布

```bash
# 构建测试环境
npm run build:stage

# 构建生产环境
npm run build:prod
```

## 其它

```bash
# 预览发布环境效果
npm run preview

# 预览发布环境效果 + 静态资源分析
npm run preview -- --report

# 代码格式检查
npm run lint

# 代码格式检查并自动修复
npm run lint -- --fix
```

[本系统基于vue-element-admin修改](https://github.com/PanJiaChen/vue-element-admin.git)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzk0Njc5NjUyXX0=
-->