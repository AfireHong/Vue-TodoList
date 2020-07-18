<!--
 * @Author: Afirehong
 * @Date: 2020-07-18 12:22:55
 * @LastEditTime: 2020-07-18 17:03:20
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \todolist\src\components\List.vue
--> 
<template>
  <ul class="todo-main">
    <TodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :index="index"
      :todo="todo"
      :delTodo="delTodo"
    />
  </ul>
</template>

<script>
import TodoItem from './TodoItem'
export default {
    name:'List',
    props:{
      todos:Array,
      delTodo:Function
    },
    components:{
      TodoItem
    }
}

</script>
<style>
.todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
  }
</style>