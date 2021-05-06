<template>
  <div>
    <h2 class ="header"> My TodoList </h2>
    
    <ul class ="ul">
      
      <li class = "li" v-bind:key="todo.id" v-for="todo in todos">
        <Todo v-bind:todo="todo" 
        v-on:delete-todo="$emit('delete-todo', todo.id)"/>
      </li>
    </ul>

  

  </div>
</template>

<script>
import Todo from './Todo';

export default {
  name: 'Todos',

  components: {
    Todo
  },

  props: [
    "todos"
  ]
  
}
</script>


<style>

ul {
  margin: 0;
  padding: 0;
}

/* Style the list items */
ul li {
  cursor: pointer;
  position: relative;
  padding: 8px 10px 9px 7px;
  list-style-type: none;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;
  
  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #f9f9f9;
}

/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}

/* When clicked on, add a background color and strike out text */
ul li.checked {
  background: #888;
  color: #fff;
  text-decoration: line-through;
}

/* Add a "checked" mark when clicked on */
ul li.checked::before {
  content: '';
  position: absolute;
  border-color: #fff;
  border-style: solid;
  border-width: 0 2px 2px 0;
  top: 15px;
  left: 16px;
  bottom: 5px;
  transform: rotate(45deg);
  height: 15px;
  width: 7px;
}

.close {
  position: center;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;
}

.close:hover {
  background-color: #f44336;
  color: white;
}

.header {
  background-color: #2a025f;
  padding: 50px 0px;
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