# 内容回顾

## vue-resource

-----------------------

# 今日内容

## 新闻详情页面

	步骤:
		1、点击newslist.vue中每一项，跳转到newsinfo.vue，并且带上新闻newsId
		
		2、根据newsId获取数据
		
		3、渲染(写html+css)

-----------------------

## 显示隐藏返回按钮和底部TabBar
	分析:
		什么时机?
			判断路由
			
		需要解决的坎？
			在路由变化的时候，获取路由，并且根据路由判断
			监控路由的变化
	
		以后工作中遇到比较复杂的业务逻辑，一定要自己把这个大的目标
		拆解成一个一个小目标，各个击破
	
	步骤：
		1、在App.vue中，通过watch方法来监控路由的变化
		
		2、根据路径，来显示或是隐藏头部的返回按钮和底部的TabBar
			v-show来显示和隐藏返回按钮
	
	
	v-if/v-show 可以达到显示&隐藏我们返回按钮和底部TabBar
	
	动态绑定样式显示和隐藏底部TabBar
		https://cn.vuejs.org/v2/guide/class-and-style.html
	
### 声明式导航&编程式导航
	声明式导航 router-link 写在html中的
	编程式导航 $router 写在js函数中的
	
	参考:https://router.vuejs.org/zh-cn/essentials/navigation.html
	
### $route&$router
	$route 获取路径path、参数
	$router 动作执行者，用来进行路由导航(前进后退)

-----------------------

## 评论子组件
	评论在新闻详情&图片详情&商品详情中都有这个功能
	把相同功能代码写在一个组件中(subcomment.vue)，该组件帮我们完成加载对应id的评论内容和提交给对应id评论内容
	
	在需要的地方（新闻详情）把我们评论组件集成进来，并且要给他传递条件，
	剩下的事情交给（subcomment.vue）
	
	步骤:
		1、先要创建一个子组件出来(subcomment.vue)
		
		2、集成到父组件中去
			2.1 在父组件中导入子组件
			2.2 在父组件的components中注册一下
			2.3 就可以在父组件的template中使用子组件了
		
		3、父组件要传递值给它是使用的子组件
			接收方:子组件
			
			发送发:父组件
		
		4、子组件获取到父组件传递过来的值，之后，做自己的业务逻辑
		
### 评论子组件业务逻辑
	1、搭建UI布局
	
	2、完成展示评论列表(加载更多)
		2.1 加载第一页
		2.2 加载更多

	3、完成提交评论的功能
	
-----------------------

## 图片分享

### 列表页面
	列表分类
		ul > li
		
### 图片详情
	获取数据
	渲染
	
	
	集成评论子组件，让其做事
		1、导入subcomment.vue
		2、在components中注册
		3、在父组件的template中使用，并且给他传值
		
	缩略图
		1、展示我们的缩略图
			1.1、获取数据
			1.2、通过九宫格布局
		
		2、预览
			https://github.com/LS1231/vue-preview
			
			可以先不用管babel-loader

-----------------------