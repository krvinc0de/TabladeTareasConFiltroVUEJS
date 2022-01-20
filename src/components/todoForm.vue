<template>
        <!-- @sunmit.prevent sirve para enviar sin refrescar tarea-->
        <form class="formulario" @submit.prevent="agregarTarea">
                <input 
                class="form-control my-2 inputText"
                type="text"
                placeholder="Create new task"
                v-model.trim = "texto"
                >
        </form>
</template>

<script>
//usamos la variable del provider con inject
import{ inject, ref, toRef} from 'vue'

export default {
        setup() {
              const tareas = inject('tareas')  
              const texto = ref('')

              const agregarTarea = () => {
                      if (texto.value === '') {
                              alert('tarea vacia')
                              return
                      }

                      const tarea = {
                              id: Date.now(),
                              texto: texto.value,
                              estado: false
                      }
                      texto.value =''

                      tareas.value.push(tarea)
                      console.log(tareas)
                      //console.log(tarea)
              }
                return{texto, agregarTarea}
        }        
}
</script>

<style scoped>
.formulario{
        border-width: 1px;
        border-color: black;
        border-radius: 5px;
        border-style: solid;
        width: 100%;
}

.inputText{
        margin-left: 5px;
}
</style>