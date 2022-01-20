<template>
        <div class="btn-group d-flex mt-3" role="group" aria-label="Basic Example">
                <button class="btn btn-primary w-100" type="button" 
                :class="{'text-info': estado === 'active'}"
                        @click="filtro('active')">
                        Activos
                </button>
                <button class="btn btn-info w-100" type="button" 
                :class="{'text-danger': estado === 'all'}"
                @click="filtro('all')">
                        todos
                </button>
                <button class="btn btn-dark w-100" type="button" 
                :class="{'text-info': estado === 'complete'}"
                @click="filtro('complete')">
                        completados
                </button>
        </div>
</template>

<script>
import { inject } from 'vue'

export default {
        setup() {
               const estado = inject("estado")
               const filtro = valor => {
                       estado.value = valor
               }

               return { estado, filtro }
        },
}
</script>