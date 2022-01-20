<template>
        <ul class="list-group">
                <todo-item v-for="item in tareas" :key="item.id" :todo="item"/>
                <todo-footer v-if="tareas.length"/>

                <li v-if="tareas.length === 0" class="list-group-item">
                        Sin tareas pendientes👌
                </li>
        </ul>
        <todo-filtro />
</template>

<script>
import { computed, inject, provide, ref} from 'vue'
import todoItem from './todoItem.vue'
import todoFooter from './todoFooter.vue'
import todoFiltro from './todoFiltro.vue'

export default {
        components:{ todoItem, todoFooter, todoFiltro},
        setup() {
              const tasks = inject('tareas')
              const estado = ref('all')

              const tareas = computed( () => {
                      if (estado.value == 'all') {
                        return tasks.value
                      }
                      if (estado.value == 'active') {
                              return tasks.value.filter(item => item.estado === false)
                      }
                      if (estado.value == 'complete') {
                              return tasks.value.filter(item => item.estado === true)
                      }
              })

              provide('estado', estado)

              return { tareas }
        }
}
</script>