# 内容回顾

## 建立最基本的文件和文件夹

## 用webpack来打包我们的源代码
	src
		main.js
		App.vue
		
	webpack.develop.config.js中的配置代码
		建议拷贝
		
	webpack --config webpack.develop.config.js

	手工创建index.html
		写id=app的div
		通过script导入bundle.js
		
## 使用`html-webpack-plugin`+`webpack-dev-server`来实现热更新
	html-webpack-plugin：以参照文件template.html在内存中生成index.html，并且会自动导入bundle.js
	
	webpack-dev-server node开启的服务器
	webpack-dev-server --config webpack.develop.config.js --progress --port 3008 --open --hot
	
## webpack & webpack-dev-server的异同
	同:
		都能打包，打包的参数，webpack中有的，webpack-dev-server都有，并且还会比它多

	不同点:
		应用场景
			webpack-dev-server 开发阶段用
			webpack 生产阶段
			
		效果不一样
			webpack-dev-server 开启一个node服务器，运行index.html&bundle.js
			
			webpack 只会生成bundle.js文件，自己运行还需要创建index.html，使用EaseServer来运行

-------------------------

# 今日内容

## 脚手架
	作用：帮我们生成项目最基本的结构，逻辑还是要自己写
	
	https://github.com/vuejs/vue-cli
	
	当你对webpack比较熟悉之后，用它比较合适
	
## App.vue
	头部
	
	中间内容
		在html中写
			router-link 写好跳转的路径
			router-view 路由的占位
			
		在js中写
			先要把组件定义好(导入组件)
			创建路由对象&设置路由规则
			把路由对象注入到根实例中，让整应用拥有路由的功能
	
	底部
	
	头部&底部使用饿了吗的前端团队推出的基于Vue的UI库
	
	如果我们有一些组件(mint-ui)在我们项目很多地方都需要使用它，这个时候，就建议在main.js中集成

### mint-ui
	Vue专题:
		https://www.awesomes.cn/subject/vue#应用-框架

	移动端WebApp：https://mint-ui.github.io/#!/zh-cn
	PC端:http://element.eleme.io/#/zh-CN
		https://www.iviewui.com/
		
	项目中集成mint-ui
	
--------------------------

## home.vue

### 轮播图
	1、请求轮播的数据
		
	2、使用轮播组件，完成轮播的功能
	
### 九宫格布局
	mui
	参考:http://dev.dcloud.net.cn/mui/ui/
	移动端的boostrap
	
	github的地址
		https://github.com/dcloudio/mui

--------------------------

## 新闻列表&新闻详情

	momentjs
	参考:
		http://momentjs.cn/

--------------------------

## 今天安装的包
	mint
		使用的地方:
			App.vue的头部和底部使用到它
		安装方式
			npm i mint-ui -S
			
	vue-router
		使用的地方:
			App.vue中间部分，使用路由
		安装方式
			npm i vue-router -S
		
	vue-resource
		使用的地方:
			home.vue中的轮播的时候
		安装方式
			npm i vue-resource -S
			
	file-loader & url-loader
		使用的地方:
			集成mui样式的时候
		安装方式
			npm i file-loader url-loader --save-dev
			
	moment
		使用的地方:
			在新闻列表中格式化时间的时候用到
		安装方式
			npm i moment -S
		