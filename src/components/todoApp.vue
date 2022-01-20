<template>
       <h1 class="my-5 text-center">Lista de tareas</h1>
       <todo-form />
       <todo-list />
</template>

<script>
import {provide, ref, watchEffect} from 'vue'
import todoForm from './todoForm.vue'
import todoList from './todoList.vue'

export default {
        components: {
                todoForm,
                todoList
        },
        setup(){
                //esto ereda tareas a todas partes
                const tareas = ref([])
                provide('tareas', tareas)

                //sirve para ver si existe la viaabl;e de forma local
                if(localStorage.getItem('tareas')){
                        tareas.value = JSON.parse(localStorage.getItem('tareas'))
                }

                watchEffect( () =>{
                        localStorage.setItem('tareas', JSON.stringify(tareas.value))
                })
        }
}
</script>