<script>
import ItemTarefa from "./ItemTarefa.vue";
export default {
  components: { ItemTarefa },
  props: ["kanban"],

  mounted() {},

  methods: {
    //apenas faz a ponte do emit entre os niveis
    moveTarefa(origem, destino, item) {
      console.log(origem, destino, item);
      this.$emit("moveTarefa", origem, destino, item);
    },
  },
};
</script>

<template>
  <div class="listaKanban">
    <div class="titulo">
      <h3>{{ kanban.titulo }}</h3>
    </div>
    <div class="listaTarefas">
      <ul>
        <li v-for="tarefa in kanban.itens" :key="tarefa.id">
          <item-tarefa
            :tarefa="tarefa"
            :kanban="kanban"
            @moveTarefa="moveTarefa"
          />
        </li>
      </ul>
    </div>
  </div>
</template>
<style>
.listaKanban {
  padding: 2px 10px;
  background-color: #e1e1e1;
  border-radius: 8px;
  min-height: 300px;
  min-width: 450px;
  max-height: 90vh;
  overflow-y: scroll;
  align-items: center;
  margin: 10px;
}

.titulo {
  text-align: center;
  font-weight: bold;
}

li {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  border-radius: 5px;
  background-color: white;
  min-height: 100px;
  width: 90%;
  margin: 3%;
  list-style: none;
  padding: 2%;
}
ul {
  padding: 0;
}
</style>
