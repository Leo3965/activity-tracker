<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuro}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Box v-if="listaEstaVazia">
          Você não está muito produtivo hoje!
        </Box>
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
import BarraLateral from '@/components/BarraLateral.vue'
import Formulario from '@/components/Formulario.vue'
import Tarefa from '@/components/Tarefa.vue'
import ITarefa from '@/interfaces/ITarefa'
import Box from "@/components/Box.vue";

export default defineComponent({
  name: 'App',
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false
    }
  },
  computed: {
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) : void {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuro: boolean) : void {
      this.modoEscuro = modoEscuro
    }
  },
  components: {
    Box,
    Tarefa,
    Formulario,
    BarraLateral
  },
});
</script>

<style>
main {
  display: flex;
}

.lista {
  padding: 1.25rem;
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
