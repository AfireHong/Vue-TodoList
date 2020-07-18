<!--
 * @Author: Afirehong
 * @Date: 2020-07-18 12:22:43
 * @LastEditTime: 2020-07-18 16:33:35
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \todolist\src\components\Header.vue
--> 
<template>
  <div class="todo-header">
    <input
      type="text"
      placeholder="请输入今天的任务清单，按回车键确认"
      v-model="title"
      @keyup.enter="addItem"
    />
  </div>
</template>

<script>
export default {
    name:'Header',
    props:{
            addTodo:Function
    },
    data(){
        return{
            title:'',
        }
    },
    methods: {
        addItem(){
            const title = this.title.trim();
            if(!title){
                alert('不能为空！');
                return
            }else{
                let todo = {title:title, finished:false};

                this.addTodo(todo);

                this.title ='';
            }
        }
    },
}

</script>
<style scope>
/*头部*/
  .todo-header input {
    width: 560px;
    height: 28px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 4px 7px;
    outline: none;
  }

  .todo-header input:focus {
    outline: none;
    border-color: rgba(255, 0, 0, 0.8);
    box-shadow: inset 0 1px 1px rgba(255, 0, 0, 0.075), 0 0 8px rgba(255, 0, 0, 0.6);
  }
</style>