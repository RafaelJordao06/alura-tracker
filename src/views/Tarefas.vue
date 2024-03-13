<template>

        <FormularioTarefa @aoSalvarTarefa="salvarTarefa"/>
        <div class="lista">
          <TarefaVue v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
          
          <BoxVue v-if="tarefas.length === 0">Você não está muito produtivo hoje.</BoxVue>
        </div>

  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  import FormularioTarefa from '../components/Formulario.vue';
  import TarefaVue from '../components/Tarefa.vue';
  import BoxVue from '../components/Box.vue';
  import ITarefa from '../interfaces/ITarefa';
  
  export default defineComponent({
    name: 'App',
    components: {
      FormularioTarefa,
      TarefaVue,
      BoxVue
    },
    data () {
      return {
        tarefas: [] as ITarefa[]
      }
    },
    methods:{
      salvarTarefa (tarefa: ITarefa) {
        this.tarefas.push(tarefa)
      }
    }
  });
  </script>
  
  <style scoped>
  
  </style>
  