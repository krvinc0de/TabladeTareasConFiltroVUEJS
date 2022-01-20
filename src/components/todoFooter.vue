<template>
        <li class="list-group-item d-flex justify-content-between aling-items-center">

                <span class="btn btn-success">
                        {{active.length}} tareas activas
                </span>
                <span class="btn btn-danger" role="button" @click="eliminarComletados">
                        Eliminar completadas
                </span>

        </li>
</template>

<script>
import {computed, inject} from 'vue'

export default {
        setup() {
                const tareas = inject('tareas')

                const active = computed(()=>{
                        return tareas.value.filter(item => item.estado === false)
                })

                const eliminarComletados = () => {
                        tareas.value = tareas.value.filter(item => !item.estado)
                }

                return{
                        active,
                        eliminarComletados
                }
        },
}
</script>