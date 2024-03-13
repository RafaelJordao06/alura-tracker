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
        <nav class="panel mt-5">
            <ul>
                <li>
                    <router-link to="/" class="link">
                        <i class="fas fa-tasks"> Tarefas</i>
                    </router-link>
                </li>
                <li>
                    <router-link to="/projetos" class="link">
                        <i class="fas fa-project-diagram">  Projetos</i>
                    </router-link>
                </li>
            </ul>
        </nav>
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

.panel li {
    margin: 8px 0;
}
.link {
    color: #fff;
    margin-left: 1rem;
}
.link i{
    padding: 1rem;
}
.link:hover {
    color: #FAF0CA;
}
.link.router-link-active {
    color: #FAF0CA;
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