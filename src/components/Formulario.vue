<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column id-8" role="form" aria-label="Formulario para ciração de uma nova tarefa">
                <input 
                    type="text" 
                    class="input" 
                    placeholder="Qual tarefa você deseja iniciar ?"
                    v-model="descricao"
                    >
            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>

        </div>
    </div>
</template>

<script lang="ts">

    import { defineComponent } from 'vue'
    import Temporizador from './Temporizador.vue'

    export default defineComponent ({
        name: 'FormularioInput',

        emits: ['aoSalvarTarefa'],

        components: {
            Temporizador
        },

        data () {
            return {
                descricao: ''
            }
        },

        methods: {
            finalizarTarefa(tempoDecorrido: number) : void {
                this.$emit('aoSalvarTarefa', {
                    duracaoEmSeundos: tempoDecorrido,
                    descricao: this.descricao 
                })
                this.descricao= '';
            }
        }
    });

</script>

<style>
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>