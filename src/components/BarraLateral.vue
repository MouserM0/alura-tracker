<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt=""/>
        </h1>
        <button class="button" @click="alterarTema">
           {{ textoDoBotao }}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data () {
        return {
            modoEscuroAtivo: false
        }
    },
    computed: {
        textoDoBotao () {
            if(this.modoEscuroAtivo) {
                return 'Desativar DarkMode'
            } 
            return 'Ativar DarkMode'
        }
    },
    methods: {
        alterarTema() {
            this.modoEscuroAtivo = !this.modoEscuroAtivo
            this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
        }
    }
})
</script>

<style scoped>
header {
    padding: 1rem;
    background: var(--bg-barra);
    width: 100%;
    height: 100vh;
    text-align: center;
}

@media only screen and (max-width: 768px){
    header {
        padding: 2.5rem;
        height: auto;
    }
}
.button {
    background-color: var(--bg-primario);
    color: var(--texto-primario);
}
</style>
