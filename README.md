# login-demo

> Login demo with token

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


## Vue最后一天 ##

- Vue基础:

	+ 插值表达式
	+ 指令
	+ 事件处理
	+ 组件
	+ 动画
	+ 过滤器
	+ watch
	+ computed
	...

- vue-router 路由

	+ 路由切换跳转前进后退,结合watch监视路由变化

	+ **导航守卫**

- vue-resource / **axios(拦截器, 模块化)**

	+ http库

- vuex

	+ 数据共享

- **JWT  使用Token做登录状态保持**

- **Element-UI   桌面端的UI组件库**

### 项目部署 ###

1. 使用`vue-cli`脚手架建立项目

	预先准备环境: node(8+) + npm + vue-cli(npm i vue-cli -g)

		vue init webpack login-demo

	注意: 如果需要开启eslint或e2e测试等, 自行选择, 这里都选了N, 只开启了vue-router, 并使用npm管理项目

	演示案例:

		PS C:\Users\LTC\Desktop> vue init webpack login-demo2

		? Project name login-demo2
		? Project description Login demo with JWT
		? Author TianchengLee <ltc6634284@gmail.com>
		? Vue build runtime
		? Install vue-router? Yes
		? Use ESLint to lint your code? No
		? Set up unit tests No
		? Setup e2e tests with Nightwatch? No
		? Should we run `npm install` for you after the project has been created? (recommended) npm
		
2. 安装less或sass

	由于脚手架默认配置好了less和sass, 但是没有安装对应的包, 可以根据需求自行选择安装

		npm i less less-loader sass-loader node-sass -D

3. 使用git/svn来管理代码

	在本地初始化仓库

		git init

	提交代码到本地

		git add .
		git commit -m "Init Project"
	
	在github中建立好仓库, 将本地仓库和github仓库进行关联并提交本地的代码到远程

		git remote add origin git@github.com:TianchengLee/login-demo.git
		git push -u origin master
	

