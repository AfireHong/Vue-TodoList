<!--
 * @Author: Afirehong
 * @Date: 2020-07-18 10:38:45
 * @LastEditTime: 2020-07-18 22:43:33
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \todolist\src\App.vue
--> 
<template>
  <div id="app">
    <div class="todo-container">
    <div class="todo-wrap">
        <Header :addTodo="addTodo"/>
        <List :todos="todos" :delTodo="delTodo"/>
        <Footer :todos="todos" :totalCount="todos.length" :selectedAll="selectedAll" :delFinishedTodo="delFinishedTodo"/>
    </div>
  </div>
  </div>
</template>

<script>
import Footer from './components/Footer'
import Header from './components/Header'
import List from './components/List'

export default {
  name: 'App',
  components: {
    Footer,
    Header,
    List
  },
  data(){
    return{
      todos:[
        {title:'任务标题1', finished:false},
        {title:'任务标题2', finished:false},
        {title:'任务标题3', finished:false},
        {title:'任务标题4', finished:false},
      ],
    }
  },
  methods: {
        addTodo(Item){
          this.todos.unshift(Item)
        },
        delTodo(index){
          this.todos.splice(index, 1)
        },
        selectedAll(isCheck){
          let todos = this.todos;
          todos.forEach(todo => {
            todo.finished = isCheck;
        })
        },
        delFinishedTodo(){
          this.todos = this.todos.filter(todo => !todo.finished)
        }
  },
   
}
</script>

<style>
body {background: #fff;}

.btn {
  display: inline-block;
  padding: 6px 10px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-warning {
  color: #fff;
  background-color: orange;
  border: none;
}

.btn-warning:hover {
  color: #fff;
  background-color: red;
}

.btn:focus {
  outline: none;
}
 /*主面板*/
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
