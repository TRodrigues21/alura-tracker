<template>
     <section>
        <strong class="display">
            {{ tempoDecorrido }}
        </strong>
    </section>
</template> 

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent ( {
    name: 'Cronometro-Segundos',

    props: {
        tempoEmSegundos: {
            type: Number,
            default: 0
        }
    },
    // Metodo para retornar uma string que vai pegar o tempo em ms e transformar em s
    computed: {
            tempoDecorrido () : string {
                return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
            }
        }
})

</script>

<style scoped>
.display{
    color: var(--texto-primario);
}
</style>