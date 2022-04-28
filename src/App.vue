<script>
import ListaTarefas from "./components/ListaTarefas.vue";
export default {
  components: { ListaTarefas },
  data() {
    return {
      kanban: {
        backlog: {
          name: "backlog",
          titulo: "Tarefas backlog",
          itens: [
            { id: 1, titulo: "item1", descritivo: "item 1 descritivo" },
            { id: 2, titulo: "item2", descritivo: "item 2 descritivo" },
            { id: 7, titulo: "item7", descritivo: "item 7 descritivo" },
            { id: 8, titulo: "item8", descritivo: "item 8 descritivo" },
          ],
          kanbanBack: null,
          kanbanNext: "todo",
        },
        todo: {
          name: "todo",
          titulo: "Tarefas todo",
          itens: [
            { id: 3, titulo: "item3", descritivo: "item 3 descritivo" },
            { id: 4, titulo: "item4", descritivo: "item 4 descritivo" },
          ],
          kanbanBack: "backlog",
          kanbanNext: "done",
        },
        done: {
          name: "done",
          titulo: "Tarefas done",
          itens: [
            { id: 5, titulo: "item5", descritivo: "item 5 descritivo" },
            { id: 6, titulo: "item6", descritivo: "item 6 descritivo" },
          ],
          kanbanBack: "todo",
          kanbanNext: null,
        },
      },
    };
  },
  methods: {
    moveTarefa(origem, destino, item) {
      //adiciona no destino
      this.kanban[destino].itens.push(item);

      //remove do kanbam atual
      const removeIndex = this.kanban[origem].itens
        .map((item) => item.id)
        .indexOf(item.id);
      this.kanban[origem].itens.splice(removeIndex, 1);
    },
  },
};
</script>

<template>
  <div class="flex">
    <div v-for="itemKanban in kanban" :key="itemKanban.name">
      <ListaTarefas :kanban="itemKanban" @moveTarefa="moveTarefa" />
    </div>
  </div>
</template>

<style>
.flex {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>
