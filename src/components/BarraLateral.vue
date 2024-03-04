<template>
    <header>
        <div class="logo">

            <h1 class="tamanho-imagem">
                <img src="@/assets/logo.png" alt="">
            </h1>
        </div>
        <div class="botao">
            <button class="button" @click="alterarTema">
                {{ textoBotao }}
            </button>
        </div>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data () {
        return {
            modoEscuroAtivo: false
        }
    },
    computed:{
        textoBotao () {
            if (this.modoEscuroAtivo){
                return 'Desativar modo escuro'
            }
            return 'Ativar modo escuro'
        }
    },
    methods:{
        alterarTema(){
            this.modoEscuroAtivo = !this.modoEscuroAtivo
            this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
        }
    }
})
</script>

<style scoped>
header {
    background: #0d3b66;
    width: 100%;
    height: 100vh;
}

.logo {
    display: flex;
    justify-content: center;
    padding-top: 1rem;

}

.tamanho-imagem {
    max-width: 6rem;
}

.botao{
    display: flex;
    justify-content: center;
    padding-top: 1rem;
}
@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }

    .logo {
        padding-top: 0rem;
        display: flex;
        justify-content: center;
    }
}
</style>