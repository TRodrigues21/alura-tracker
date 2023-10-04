<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descição'}}
            </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSeundos"/>
            </div>
        </div>
    </Box>
</template>

<script lang="ts">

import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue'
import ITarefa from '@/interfaces/ITarefa';
import Box from './Box.vue';

export default defineComponent ( {
    name: 'Lista-Tarefas',

    components: {
        Cronometro,
        Box
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
}) 
</script>

