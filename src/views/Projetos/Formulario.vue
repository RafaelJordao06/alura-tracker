<template>
    <section>
        <form @submit.prevent="salvar">
            <div class="field">
                <label for="nomeDoProjeto" class="label"> Nome do Projeto</label>
                <input type="text" class="input" v-model="nomeDoProjeto" id="nomeDoProjeto" />
            </div>
            <div class="field">
                <button class="button" type="submit" :disabled="nomeDoProjeto.length <= 0">Salvar</button>
            </div>
        </form>
    </section>
</template>
<script lang="ts">
import { TipoNotificacao } from '@/interfaces/INotificacao';
import { useStore } from '@/store';
import useNotificador from '@/hooks/notificador'
import { ADICIONA_PROJETO, ALTERAR_PROJETO } from '@/store/tipo-mutacoes';
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'FormularioVue',
    props: {
        id: {
            type: String
        }
    },
    mounted() {
        if (this.id) {
            //Procuro na minha store o meu projeto com o id
            const projeto = this.store.state.projetos.find(proj => proj.id == this.id)
            this.nomeDoProjeto = projeto?.nome || ''
        }
    },
    data() {
        return {
            nomeDoProjeto: ""
        };
    },
    methods: {
        salvar() {
            if (this.id) {
                this.store.commit(ALTERAR_PROJETO, {
                    id: this.id,
                    nome: this.nomeDoProjeto
                })
            } else {
                this.store.commit(ADICIONA_PROJETO, this.nomeDoProjeto)
            }
            this.nomeDoProjeto = '';
            this.notificar(TipoNotificacao.SUCESSO, "Execelente!", "O projeto foi cadastro com sucesso!")
            this.$router.push('/projetos')
        }

    },
    setup() {
        const store = useStore()
        const { notificar } = useNotificador()
        return {
            store,
            notificar
        }
    }
})
</script>
