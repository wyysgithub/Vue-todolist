# Vue.js实现todolist功能

[Vue.js官方文档](https://cn.vuejs.org)


文件：[index.html](https://github.com/wyysgithub/Vue-todolist/blob/master/index.html)


## 项目简介

#### 1，界面

![](https://github.com/wyysgithub/Vue-todolist/blob/master/img/d-1.png)

#### 2，添加

* 输入之后，点击添加即可。

![](https://github.com/wyysgithub/Vue-todolist/blob/master/img/d-2.png)
![](https://github.com/wyysgithub/Vue-todolist/blob/master/img/d-3.png)

日志会记录添加时间。

#### 3，删除

* 直接在列表项里点击删除，弹出提示，确认，则删除成功。

![](https://github.com/wyysgithub/Vue-todolist/blob/master/img/d-4.png)

* 记录日志。

![](https://github.com/wyysgithub/Vue-todolist/blob/master/img/d-5.png)

直接点击删除按钮，则会删除最近添加的一个列表项。

![](https://github.com/wyysgithub/Vue-todolist/blob/master/img/d-6.png)






## 知识点总结：

#### 1，定义局部组件

```
/*局部组件*/
		/*每个组件都是Vue的一个实例*/
		var TodoItem={
			template:"<li>这是一个局部组件</li>"
		}
```

定义的局部组件，需要注册后才能使用
```
/*要使用局部组件，需要注册*/
	new Vue({
			el:"#root",
			components:{
				'todo-item': TodoItem
			}
			})
```

#### 2，全局组件

```
/*Vue.component()定义的组件为全局组件*/
		Vue.component("todoitem-g",{
			/*接收父级传送的属性*/
			props:['content','index'],
			template: '<p class="w-h" @click="deletethis">{{content}}<br><small>{{getDate()}}</small></p>',
			methods:{
				deletethis:function(){
					/*触发一个delete事件，值为this.index*/
					this.$emit('delete',this.index)
				},
				getDate:function(){
					var newDate=new Date();
					return newDate.toLocaleString();
				},
			}
		})
```

* 第一个参数为组件名，可在html中用'<todoitem-g></todoitem-g>'调用组件。

* props 用来接收父级实例传送的属性

* template 用来定义模版内容

* methods 用来定义函数

```
this.$emit('delete',this.index)
```
定义一个delete事件，值为this.index。

父级可用"@delete="deleteThis"进一步触发根实例中的deleteThis函数。

#### 3，其他知识点

* 数组操作：


https://blog.csdn.net/gj1949/article/details/54138303

https://blog.csdn.net/lcl19970203/article/details/54562393
