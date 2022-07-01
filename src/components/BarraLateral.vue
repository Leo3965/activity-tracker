<template>
  <header>
    <h1>
      <img src="../assets/araras.png" class="logo" alt="logo da vue">
    </h1>
    <button class="button" @click="alterarTema">
      <img :src="iconePath" class="dark-mode-button"/>
    </button>
  </header>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: 'BarraLateral1',
  emits: ['aoTemaAlterado'],
  data() {
    return {
      modoEscuro: false,
      iconePath: require(`../assets/sunny-outline.svg`)
    }
  },
  computed: {
    textoBotao() {
      if (this.modoEscuro) {
        return 'Desativar modo escuro'
      }
      return 'Ativar modo escuro'
    }
  },
  methods: {
    alterarTema() {
      this.modoEscuro = !this.modoEscuro
      this.$emit('aoTemaAlterado', this.modoEscuro)
    },
    alterarIcone(): void {
      if (this.modoEscuro) {
        //this.iconePath = 'https://i.imgur.com/2RJTr2f.png'
        this.iconePath = require(`../assets/sunny-outline.svg`);
      } else {
        this.iconePath = 'https://i.imgur.com/ApvguGb.png'
      }
    }
  }
})
</script>

<style scoped>
/* Todo o estilo do componente */
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  justify-content: center;
  text-align: center;
}

h1 {
  display: flex;
  justify-content: center;
}

.logo {
  max-width: 85%;
  border-radius: 30px;
  margin-bottom: 1rem;
}

button {
  padding: 1.6rem 0.2rem 1.6rem 0.2rem;
  border-radius: 67%;
  background-color: var(--bg-primaria);
}

.dark-mode-button {
  width: 3rem;
  filter: ;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
  }
}
</style>