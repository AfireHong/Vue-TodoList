<!--
 * @Author: Afirehong
 * @Date: 2020-07-18 12:23:16
 * @LastEditTime: 2020-07-18 17:08:26
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \todolist\src\components\Item.vue
--> 
<template>
  <li @mouseover="mouseOver(true)" @mouseleave="mouseLeave(false)" :class="{bgColor:hover}">
    <label>
      <input type="checkbox" v-model="todo.finished" />
      <span>{{todo.title}}</span>
    </label>
    <button v-show="hover" @click="delItem" class="btn btn-warning">删除</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object,
    delTodo: Function,
    index: Number
  },
  data() {
    return {
      hover: false
    };
  },
  methods: {
    mouseOver() {
      this.hover = true;
    },
    mouseLeave() {
      this.hover = false;
    },
    delItem() {
        
       this.delTodo(this.index); 
    }
  }
};
</script>
<style scope>
/*列表选项*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}
.bgColor {
  background: #ddd;
}
li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}
li button {
  background-color: orangered;
  padding: 4px 10px;
  border-radius: 5px;
  color: #fff;
  border: none;
  float: right;
  margin-top: 3px;
  outline: none;
  cursor: pointer;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>
