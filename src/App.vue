<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoAlterarTema="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
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
      tarefas: [] as Itarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: Itarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema(ativo: boolean) {
      console.log(ativo);
      this.modoEscuroAtivo = ativo;
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #f5f5f5;
  --texto-primario: #363636;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
  color: var(--texto-primario);
}
</style>
