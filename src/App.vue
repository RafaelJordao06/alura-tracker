<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Notificacoes></Notificacoes>
      <RouterView></RouterView>
    </div>

  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Notificacoes from './components/Notificacoes.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Notificacoes
  },
  data () {
    return {
      modoEscuroAtivo: false
    }
  },
  methods:{
    trocarTema (modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style scoped>
.lista{
  padding: 1.25rem;
}
main{
  --bg-primary: #fff; 
  --text-primary: #000; 
}
main.modo-escuro{
  --bg-primary: #2b2d42; 
  --text-primary: #ddd; 
}
.conteudo{
  background-color: var(--bg-primary);
}
</style>
