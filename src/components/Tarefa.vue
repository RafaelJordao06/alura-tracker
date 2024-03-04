<template>
    <BoxVue>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroVue :tempoEmSegundo="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxVue>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue';
import CronometroVue from './Cronometro.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxVue from './Box.vue';

export default defineComponent({
    name: 'TarefaVue',
    components:{
        CronometroVue,
        BoxVue
    },
    props:{
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})

</script>

