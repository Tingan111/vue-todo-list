<script setup>
import {ref} from "vue"
let id=0
const newTodo=ref('')
const Todos=ref([
  {id:id++,content:"第一名"},
  {id:id++,content:"第二名"},
  {id:id++,content:"第三名"},
])
function addTodo(){
  Todos.value.push({id:id++,content:newTodo.value})
  newTodo.value=""
}
function removeTodo(todo){
Todos.value=Todos.value.filter((t)=>t!=todo)

}

</script>
<template><form @submit.prevent="addTodo">
  <input v-model="newTodo" required placeholder="new todo">
  <button>新增</button>
  <ul>
    <li v-for="todo in Todos" :key="todo.id">{{ todo.id }},{{ todo.content }}
      <button @click="removeTodo(todo)">X</button>

    </li>
  </ul>
   
</form>
</template>