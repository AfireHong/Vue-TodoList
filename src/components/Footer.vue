<!--
 * @Author: Afirehong
 * @Date: 2020-07-18 12:23:41
 * @LastEditTime: 2020-07-18 22:44:38
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \todolist\src\components\Footer.vue
--> 
<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="isCheck"/>
    </label>
    <span>
          <span>已完成{{finishedCount}}件</span> / 总计{{totalCount}}件
        </span>
    <button class="btn btn-warning" @click="delFinishedTodo">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name:'Footer',
  props:{
      totalCount:Number,
      todos:Array,
      selectedAll:Function,
      delFinishedTodo:Function
  },
  computed: {
        finishedCount(){
          return this.todos.reduce((total, value) => total + (value.finished ? 1 : 0),0);
        },
        isCheck:{
          get(){
            return this.todos.length == this.finishedCount && this.todos.length>0;
          },
          set(value){
            this.selectedAll(value);
          }
        }
  }, 
}

</script>
<style>
/*尾部*/
  .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
  }

  .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
  }

  .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
  }

  .todo-footer button {
    float: right;
    margin-top: 5px;
  }
</style>