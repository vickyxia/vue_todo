<template>
  <div id="app">
   
    <mytitle></mytitle>
    <todo></todo>
    <myfooter></myfooter>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import mytitle from './components/mytitle.vue'
import todo from './components/todo.vue'
import myfooter from './components/myfooter.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    mytitle,
    todo,
    myfooter
  }
}
</script>

<style>
#app {
  position:absolute;
  left:0;
  right: 0;
  top:0;
  bottom: 0;
}

</style>
