<template>
  <BoxWrapper>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
        <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </BoxWrapper>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Cronometro from './CronometroTarefa.vue';
import Itarefa from '../interfaces/ITarefa'
import BoxWrapper from './BoxWrapper.vue';

export default defineComponent({
  name: 'TarefaComp',
  components: {
    Cronometro,
    BoxWrapper
  },
  props: {
    tarefa: {
      type: Object as PropType<Itarefa>,
      required: true
    }
  }
});
</script>