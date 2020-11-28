<template>
  <form @submit.prevent="formulario">
      <input 
        type="text"
        class="form-control my-3"
        placeholder="Ingrese Tarea"
        v-model.trim="texto"
      >
  </form>
</template>

<script>
import { inject, ref } from 'vue'
export default {
    setup(){
        const todos = inject('todos')
        console.log(todos.value)
        
        const texto = ref('')

        const formulario = () => {
            console.log('diste click')

            // Validamos que no este vacio o que haya ingresado solo espacios
            if(texto.value === ''){
                console.log('Esta vacio')
                return
            }

            console.log(texto.value)

            const todo = {
                texto: texto.value,
                completada: false,
                id: Date.now()
            }
            todos.value.push(todo)
            console.log(todos)

            texto.value = ''
            console.log(todo)

        }
        return { formulario, texto }
        
    }

}
</script>

<style>

</style>