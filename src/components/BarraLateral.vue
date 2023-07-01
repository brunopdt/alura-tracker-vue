<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Alura Tracker logo">
    </h1>

    <button class="button" @click="alterarTema">
      <span class="icon">
        <i class="fas" :class="iconeBotao"></i>
      </span>
    </button>

  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BarraLateral',
  emits: ['aoAlterarTema'],
  data() {
    return {
      temaEscuro: false
    }
  },
  computed: {
    iconeBotao() {
      if (this.temaEscuro) {
        return 'fa-sun'
      } else {
        return 'fa-moon'
      }
    }
  },
  methods: {
    alterarTema() {
      this.temaEscuro = !this.temaEscuro
      this.$emit('aoAlterarTema', this.temaEscuro)
    }
  }
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;

  >h1 {
    margin-bottom: 2rem;
  }
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>