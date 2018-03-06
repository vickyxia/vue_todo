<template>
<section class="real-app">
	<input 
		type="text" 
		class="add-input"
		@keyup.enter = "addToList"
		autofocus="autofocus"
		placeholder="What to do now?" 
	/>
	<item 
		v-for="todo in filteredTodos" 
		:todo="todo" 
		:key="todo.id" 
		@del="deleteTodo"
	/>
	<tabs 
		:filter = "filter"
		:todos="todos"
		@toggle="toggleFilter"
		@clearAll="clearAll"
	/>
	
</section>
</template>

<script>
import Item from './item.vue'
import Tabs from './tabs.vue'

let id=0
export default {
	data() {
		return {
			todos:[],
			filter: "all"
		}
		
	},
	methods: {
		addToList(e) {
			this.todos.unshift({   // 点击事件时内容添加到todos第一个位置
				id: id++,   // 列表数目
				content: e.target.value.trim(),   // 点击事件把input内容value放到content变量
				completed: false
			})
			e.target.value = ''   // 清空input
		},
		deleteTodo(id){
			this.todos.splice(this.todos.findIndex(todo => todo.id === id),1)  // delete id item
		},
		toggleFilter(state) {   // 改变过滤器内容
			this.filter = state
		},
		clearAll() {
			this.todos = this.todos.filter(todo => !todo.completed)
		}
	},
	computed: {
		filteredTodos() {
			if (this.filter === 'all'){   // 如果选的是All
				return this.todos
			}
			const completed = this.filter === 'completed'  //　判断过滤选项选的哪个
			return this.todos.filter(todo => completed === todo.completed)  // 参数，return值
		}
	},
	components: {
		Item,
		Tabs
	}

}
</script>

<style >
.real-app{
	background-color: red;
	width: 600px;
	margin:0 auto;
	box-shadow: 0 0 5px #666
}
.add-input{
	position: relative;
	margin:0;
	width: 100%;
	padding:16px 16px;
	font-size: inherit;
	border:0;
	outline: none;
	color: inherit;
	box-shadow: inset 0 -1px 5px 0 rgba(0, 0, 0, 0.2);
	box-sizing: border-box;
	border:none;
}

</style>
