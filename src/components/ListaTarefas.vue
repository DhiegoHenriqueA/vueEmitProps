<script>
export default {
  props: ["kanban"],

  mounted() {},
};
</script>

<template>
  <h3>{{ kanban.titulo }}</h3>
  <ul>
    <li v-for="tarefa in kanban.itens" :key="tarefa.id">
      {{ tarefa.titulo }}
      {{ kanban.kanbanNext }}
      <div v-if="kanban.kanbanNext">
        <input
          type="button"
          value="next"
          @click="$emit('moveTarefa', kanban.name, kanban.kanbanNext, tarefa)"
        />
      </div>
      {{ kanban.kanbanBack }}
      <div v-if="kanban.kanbanBack">
        <input
          type="button"
          value="back"
          @click="$emit('moveTarefa', kanban.name, kanban.kanbanBack, tarefa)"
        />
      </div>
    </li>
  </ul>
</template>
