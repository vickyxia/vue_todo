<template>
	<div class="helper">
		<span class="left">{{unfinishedNum}} items here</span>
		<span class="tabs">
		<span 
			v-for="state in states"
			:key ="state"
			:class = "[state, filter=== state ? 'actived': '']"
			@click = "toggleFilter(state)"
		>
		{{state}}
		</span></span>
		<span @click="clear" class="clear">Clear All Finished</span>
	</div>
</template>
<script>
export default {
	props: {   // 父组件传来的数据，本组件要用的
		todos:{
			type: Array,
			required: true,
		},
		filter: {
			type: String,
			required: true,
		}
	},
	data() {   //自己的数据
		return {
			states:['all', 'active', 'completed']
		}

	},
	computed: {
		unfinishedNum() {
			return this.todos.filter(todo=> !todo.completed ).length
		}
	},
	methods: {
		clear() {
			this.$emit("clearAll")
		},
		toggleFilter(state){
			this.$emit("toggle",state)  //传给父组件进行处理，把state传过去,到父组件那边处理@toggle，自定义事件
		}
	}

}

</script>
<style lang="stylus" scoped>
.helper{
  font-weight 100
  display flex
  justify-content space-between
  padding 5px 0
  line-height 30px
  background-color #fff
  font-size 14px
  font-smoothing: antialiased
}
.left, .clear, .tabs{
  padding 0 10px
  box-sizing border-box
}
.left, .clear{
  width 150px
}
.left{
  text-align left
}
.clear{
  text-align right
  cursor pointer
}
.tabs{
  width 200px
  display flex
  justify-content space-around
  * {
    display inline-block
    padding 0 10px
    cursor pointer
    border 1px solid rgba(175,47,47,0)
    &.actived{
      border-color rgba(175,47,47,0.4)
      border-radius 5px
    }
  }
}
</style>