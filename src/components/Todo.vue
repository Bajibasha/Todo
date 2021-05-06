<template>
   
   <div v-bind:class="{'completed': todo.completed }">
<!--    <p v-on:click="markComplete"> {{ todo.title }} </p>  -->

    <p class="ul"
         contenteditable="true"
          v-on:keydown.enter="updateTask($event, todo)"
          v-on:blur="updateTask($event, todo)"
          v-bind:class="{completed: todo.isComplete}"> {{ todo.title }} </p>


   <span class ="close" @click="$emit('delete-todo', todo)">&times;</span>  
   
   </div>
  
</template>



<script>
export default {
  name: 'Todo',
  props:[
      "todo"
  ],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed
    },
    updateTask: function(e, todo){
            e.preventDefault();
            todo.title = e.target.innerText;
            e.target.blur();
          }
  
  }
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
  padding: 8px 10px 0px 16px;
}

.close:hover {
  background-color: #f44336;
  color: white;
}

.edit {
  position: left;
  right: 0;
  top: 0;
  padding: 4px 10px 0px 16px;
}

.edit:hover {
  background-color: #05038a;
  color: white;
}
.completed {
    text-decoration: line-through;
}

</style>