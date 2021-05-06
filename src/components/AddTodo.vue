<template>
<div>
  <div>
    <form @submit="addTodo" class = "header">
      <input type="text" class="input" v-model="title" name="title">
      <button class = "addBtn" type="submit">Add</button>
    </form>

  </div>

  </div>
</template>

<script>
import *as uuid  from 'uuid';

export default {
  name: 'AddTodo',
  data() {
    return { 
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      const newTodoObj = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      }
      this.$emit('add-todo', newTodoObj);
      this.addTodo = '';
    },
    
  }
}
</script>

<style>
*{ 
  box-sizing: border-box;
}
.button0 {
  background-color: #f8f7fc;
  border: none;
  color: rgb(12, 0, 0);
  padding: 15px 32px;
  text-align: left;
  
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}

input {
  margin: px;
  border: none;
  border-radius: 0;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 16px;
}

/* Style the "Add" button */
.addBtn {
  padding: 8.5px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}

.addBtn:hover {
  background-color: #bbb;
}
.header {
  background-color: #2a025f;
  padding: 20px 40px;
  color: white;
  text-align: center;
}

/* Clear floats after the header */
.header:after {
  content: "";
  display: table;
  clear: both;
}


</style>