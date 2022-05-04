<script>
export default {
  props: ["tarefa", "kanban"],

  mounted() {},
};
</script>

<template>
  <div class="titulo">{{ tarefa.titulo }}</div>
  <div>{{ tarefa.descritivo }}</div>
  <div class="btns-end">
    <input
      v-if="kanban.kanbanBack"
      type="button"
      class="btn btn-danger"
      value="< back"
      @click="$emit('moveTarefa', kanban.name, kanban.kanbanBack, tarefa)"
    />
    <input
      v-if="kanban.kanbanNext"
      type="button"
      value="next >"
      class="btn btn-success"
      @click="$emit('moveTarefa', kanban.name, kanban.kanbanNext, tarefa)"
    />
  </div>
</template>

<style>
.btn {
  padding: 5px;
  border: 0;
  border-radius: 3px;
}
.btns-end {
  justify-content: end;
  display: flex;
  flex-direction: row;
}
.btn-success {
  background-color: green;
  color: white;
}
.btn-danger {
  background-color: #ab1d1d;
  color: white;
}
</style>
