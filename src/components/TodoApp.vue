<template>
  <h1>ToDoS</h1>

  <todo-form/>
  <todo-list />

</template>

<script>
import {provide, ref, watchEffect} from 'vue'
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'
export default {
  components: { TodoForm, TodoList },
  setup(){
      const todos = ref([])
      provide('todos',todos)

      if(localStorage.getItem('todos')){ //Pregunta si existe esa key
        todos.value = JSON.parse(localStorage.getItem('todos'))

      } 

        // Hace seguimiento a un objeto cuando cambie
      watchEffect(() => {
          console.log(todos.value.length)
          console.log(todos)
          localStorage.setItem('todos', JSON.stringify(todos.value))
      })
  }


}
</script>

<style>

</style>