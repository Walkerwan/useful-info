# 内容回顾

## MVVM
	View: id=app 的div
	Model:模型，提供数据的，在vm的一个属性 data，注意，在component中data必须是函数，并且函数里面要返回对象
	View-Model: Vue实例/Vue对象，一般项目中只有一个Vue实例，称之为根实例
	
## 指令
	作用:尽可能少的操作dom，把精力放在业务逻辑上(数据)
	{{}}插值表达式
	v-text/v-html
	v-on
	v-bind 单向数据绑定 model--->view
	v-model 双向 model--->view  view--->model
	v-if/v-show
	v-for
	
## 组件
	把一些功能相似的代码(渲染页面，网络请求，样式)放在一个文件中(.vue)，我们把这个文件就称之为组件
	
	好处:
		复用性强
		对id=app 不用写很多散的代码在里面
		
	组件的五中写法
	1、先定义，再注册，再使用
	2、定义注册一步到位，再使用
	3、对我们定义组件时候的template的优化---template
	4、对我们定义组件时候的template的优化---script
	
	5、单文件组件 .vue
		tempalte 写html代码
		style 样式代码
		script 业务逻辑，发送网络请求，接收用户点击等

## 过滤器
	私有
		组件的filters里面
		
	全局
		Vue.filter('过滤器名称',处理函数)
		
	1、过滤器其实是函数，他一定要接收一个参数，并且第一个参数是`|`前面的内容
	2、他必须要将过滤之后的结果通过return返回回去
	
## 路由
	html
		router-link 超链接
		router-view 路由占位
	
	js
		定义组件/导入写好的组件
		创建路由对象，设置路由规则
		在根实例中注入路由对象，让整个应用拥有路由功能
		
## vue-resource
	
	参考:https://github.com/pagekit/vue-resource
	
	this.$http.get(url).then(成功的回调，失败的回调)
	this.$http.post(url,{请求体},{emulateJSON:true}).then(成功的回调，失败的回调)
	this.$http.jsonp(url).then(成功的回调，失败的回调)

----------------------------

# 今日课程目标

## Webpack
	参考：http://zhaoda.net/webpack-handbook/
		http://www.jianshu.com/p/42e11515c10f
		
	webpack1.x和2.x的升级对比
	https://segmentfault.com/a/1190000008181955

### 概念
	Webpack 是当下最热门的前端资源模块化管理和打包工
	具。它可以将许多松散的模块按照依赖和规则打包成符合
	生产环境部署的前端资源。还可以将按需加载的模块进行
	代码分隔，等到实际需要的时候再异步加载。通过 
	loader 的转换，任何形式的资源都可以视作模块，比如
	CommonJs 模块、 AMD 模块、 ES6 模块、CSS、图片、
	JSON、Coffeescript、 LESS 等。
	
	通过webpack能够对我们项目的所有模块进行打包，把它变成符合生产环境的静态资源

## 核心概念
	webpack1的文档:http://webpack.github.io/docs/
	webpack2的文档:https://doc.webpack-china.org/
	
	核心概念参考:https://doc.webpack-china.org/concepts/
	
	入口:项目打包的入口，一般我们只需要打包依赖的根文件
	
	出口:一般是吧所有的模块打包之后，生成一个叫做bundle.js的文件
	
	Loader:默认情况下，webpack只能打包.js结尾的文件（模块），要打包其它其它后缀的文件，需要使用对应的loader(参考:https://doc.webpack-china.org/loaders/)
	
	插件:让我们的webpack更加牛逼
		webpack内置很多插件
		
	配置文件:为了简化我们打包的指令
	
## 使用
	参考:http://zhaoda.net/webpack-handbook/usage.html
	
	1、打包单个js文件
		1.1、写好entry.js文件的内容
		1.2、使用`webpack entry.js bundle.js`打包
		1.3、新建一个index.html，通过script导入bundle.js
		1.4、运行index.html就可以看到效果啦
		
		注意:在html中导入的是打包之后的文件，不是源文件
		
	2、打包多个js文件(多个js文件之间有依赖关系)
		2.1、写好entry.js 和 module.js文件的内容
		2.2、在entry.js导入module.js并且使用
		2.3、使用`webpack entry.js bundle.js`打包
		2.4、新建一个index.html，通过script导入bundle.js
		2.5、运行index.html就可以看到效果啦
		
		注意:在html中导入的是打包之后的文件，不是源文件
		
	3、打包非js文件(以.css为例)
		2.1、写好entry.js、module.js、site.css文件的内容
		2.2 在entry.js导入module.js、site.css并且使用
		2.3 在entry.js中导入site.css的使用，要这样写
			require('!style-loader!css-loader!./site.css')
		2.4、使用`webpack 入口文件 出口文件`打包
		2.5、新建一个index.html，通过script导入bundle.js
		2.6、运行index.html就可以看到效果啦
		
		注意：如果你不想在入口文件导入css的时候，前面加上`!style-loader!css-loader!`可以在打包的时候，在我们输出文件的后面加上 --module-bind "css=style-loader!css-loader"
		例如
			webpack entry.js bundle.js --module-bind "css=style-loader!css-loader" 注意window下用`""`
		
## webpack.config.js 配置文件
	作用:简化打包指令
	
	1、在项目根目录创建一个`webpack.config.js`
	2、在webpack.config.js中配置好入口、出口、loaders、plugins等等
		拷贝，因为自己写非常容易写错

## 插件的使用(webpack本地包自带的)
	使用注意：
		plugins是和entry、output、module同级的不要搞错了
		
## webpack打包时候的参数
	webpack --progress 查看打包进度的
	webpack --config 指定webpack的打包的配置文件
	webpack --watch【了解】监控源代码更改，重新打包，不会刷新浏览器
	webpack -p【了解】 打包的时候，顺便压缩
	
	
	注意事项:webpack后面可以同时接多个参数，并且参数之间没有先后顺序之分

-----------------------------

## 使用Webpack构建Vue项目(纯手工)

### 先把项目的基本结构搭建出来（在页面上看到`Hello Vue`）
	1、创建必要的文件和文件夹
		szhmqd10vue
			src
				main.js项目打包的入口文件
				App.vue项目启动之后看到的第一个页面
				
			package.json 项目的配置文件
			webpack.develop.config.js 开发阶段使用的webpack配置文件
		
	2、App.vue、main.js、webpack.develop.config.js写内容
		App.vue
			template:组件显示的内容写在这里
			
		main.js
			1、导入App.vue
			2、安装vue这个第三方包 npm i vue --save
	

### webpack打包bundle.js把内容呈现出来（回顾上午讲的内容）
	1、先打包成bundle.js
		1.1、在webpack.develop.config.js中写好配置的代码
		1.2、安装 vue-loader vue-template-compiler css-loader 这几个包
		说明，因为项目中到时候肯定要用到css文件，所有我就索性把style-loader装了
		1.3 使用`webpack --progress --config webpack.develop.config.js`
	
	2、创建一个index.html，然后导入bundle.js运行

### 使用webpack-dev-server&html-webpack-plugin实现所见即所得
	目的:运行项目的时候，让其在浏览器的内容中生成bundle.js和index.html，然后当我们更改了我们项目的源代码(App.vue)，实现热更新
	
	html-webpack-plugin 
		在内存中根据模版文件生成一个index.html，并且自动导入生成bundle.js
		
		1、先安装 html-webpack-plugin webpack webpack-dev-server
		2、在项目根目录创建模版页面 template.html
			在这里面写id=app的div的代码即可，不要写导入bundle.js
			
		3、在webpack.develop.config.js中写
			参考:https://github.com/jantimon/html-webpack-plugin
			```
				new HtmlWebpackPlugin({
		            template:'./template.html',
		            filename: 'index.html'
		        })
			```
	
	webpack-dev-server 全局包
		在内存中打包生成bundle.js，把我们的index.html和bundle.js运行起来
		并且实现热更新
	
		没有实现热更新打包的指令
			webpack-dev-server --progress --config webpack.develop.config.js 
			
		优化
			webpack-dev-server --progress --config webpack.develop.config.js --port 3008 --open --hot
	
-----------------------------

## webpack-dev-server 和 webpack 有啥关系呢?
	webpack-dev-server&webpack
	
	相同点:
		都能进行打包，webpack有的功能，webpack-dev-server都有，并且还有些功能是webpack不具备了(比如热更新)
		
		webpack --progress --config xxxx
		webpack-dev-server --progress --config xxxx
		
	区别:
		应用场景不一样
		
			webpack-dev-sever 用在开发阶段，在浏览器内存中生成bundle.js
			
			webpack 用在生产阶段，它会在项目dist目录下面生成一个实实在在的bundle.js
			
		产生的效果不一样
			webpack-dev-server 打包之后，除了在内存中生成一个bundle.js文件，它还会开启一个Node服务，来运行我们的index.html和bundle.js
			
			webpack 打包之后，不会开启服务运行我们的index.html和bundle.js，这个必须要借助于VSCode Ease Server

-----------------------------

## 今天安装的第三方包有哪些?
	vue 
		在哪里用到:
			main.js中我们去要渲染App.vue的时候，需要用到
		安装方式:
			cnpm i vue --save
			
	vue-loader vue-template-compiler css-loader
		在哪里用到:
			打包.vue文件的时候用到
		安装方式:
			npm i vue-loader vue-template-compiler css-loader --save-dev

	html-webpack-plugin webpack webpack-dev-server
		在哪里用到:
			根据模版文件，在内存中生成一个index.html
		安装方式:
			npm i html-webpack-plugin webpack webpack-dev-server --save-dev
		