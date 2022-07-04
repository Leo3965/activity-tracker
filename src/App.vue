<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuro}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <!-- Aqui vai a VIEW CORRESPONDENTE -->
      <router-view></router-view>
    </div>
  </main>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
import BarraLateral from '@/components/BarraLateral.vue'

export default defineComponent({
  name: 'App',
  data() {
    return {
      modoEscuro: false
    }
  },
  methods: {
    trocarTema(modoEscuro: boolean): void {
      this.modoEscuro = modoEscuro
    }
  },
  components: {
    BarraLateral
  },
});
</script>

<style>
main {
  display: flex;
}

main {
  --bg-primaria: #FFF;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primaria: #2B2B42;
  --texto-primario: #DDD
}

.conteudo {
  background: var(--bg-primaria);
}
</style>
