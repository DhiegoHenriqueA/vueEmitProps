<script>
export default {
  props: ["kanban"],

  mounted() {},
};
</script>

<template>
  <div class="listaKanban">
    <div class="titulo">
      <h3>{{ kanban.titulo }}</h3>
    </div>
    <ul>
      <li v-for="tarefa in kanban.itens" :key="tarefa.id">
        {{ tarefa.titulo }}
        <div v-if="kanban.kanbanNext">
          <input
            type="button"
            value="next"
            @click="$emit('moveTarefa', kanban.name, kanban.kanbanNext, tarefa)"
          />
        </div>
        <div v-if="kanban.kanbanBack">
          <input
            type="button"
            value="back"
            @click="$emit('moveTarefa', kanban.name, kanban.kanbanBack, tarefa)"
          />
        </div>
      </li>
    </ul>
  </div>
</template>
<style>
.listaKanban {
  padding: 2px 15px;
  background-color: beige;
  border-radius: 8px;
  min-height: 300px;
  min-width: 300px;
  align-items: center;
}

.titulo {
  background-color: darkblue;
  color: white;
  text-align: center;
}
</style>
