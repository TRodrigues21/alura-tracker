<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">

        <Cronometro :tempoEmSegundos="tempoEmSegundos"/>
        <Botao @clicado="iniciar" icone="fas fa-play" texto="Play" :desabilitado=cronometroRodando />         
        <Botao @clicado="finalizar" icone="fas fa-stop" texto="Stop" :desabilitado=!cronometroRodando />
                    
    </section>
</template>

<script lang="ts">

    import { defineComponent } from 'vue'
    import Cronometro from './Cronometro.vue'
    import Botao from './Botao.vue'

    export default defineComponent ({
        name: 'Temporizador-Segundos',

        emits: ['aoTemporizadorFinalizado'],

        components: {
            Cronometro,
            Botao
        },

        // Metodo para contar os segundos
        data () {
            return { // Retorna um obeto 
                // Objeto que representa quais as informações desse compinente
                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroRodando: false
            }
        },

        // Metodos 
        methods: {
            // Para inciar o cronometro
            iniciar() {
                this.cronometroRodando = true;
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos += 1;
                }, 1000)
            }, 
            // Para finalizar o cronometro
            finalizar() {
                this.cronometroRodando = false;
                clearInterval(this.cronometro);
                this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
                this.tempoEmSegundos = 0;
            }
        }
    });

</script>