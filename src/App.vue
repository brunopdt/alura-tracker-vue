<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">

        <TarefaComp v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />

        <BoxWrapper v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </BoxWrapper>

      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import TarefaComp from './components/TarefaComp.vue';
import Itarefa from './interfaces/ITarefa'
import BoxWrapper from './components/BoxWrapper.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaComp,
    BoxWrapper
  },
  data() {
    return {
      tarefas: [] as Itarefa[]
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: Itarefa) {
      this.tarefas.push(tarefa)
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
</style>
