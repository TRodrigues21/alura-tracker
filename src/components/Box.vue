<template>
    <div class="box has-text-weight-boldv" :style="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'Componente-Box',
    data () {
        return {
            estilos: {
                background: '#FAF0CA'
            }
        }
    }
})
</script>

