<script>
import ListaTarefas from "./components/ListaTarefas.vue";
export default {
  components: { ListaTarefas },
  data() {
    return {
      kanban: {
        todo: {
          name: "todo",
          titulo: "tarefas todo",
          itens: [
            { id: 1, titulo: "item1", descritivo: "item 1 descritivo" },
            { id: 2, titulo: "item2", descritivo: "item 2 descritivo" },
          ],
          kanbanBack: null,
          kanbanNext: "done",
        },
        done: {
          name: "done",
          titulo: "tarefas done",
          itens: [
            { id: 1, titulo: "item3", descritivo: "item 1 descritivo" },
            { id: 2, titulo: "item4", descritivo: "item 2 descritivo" },
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
  <ListaTarefas :kanban="kanban.todo" @moveTarefa="moveTarefa" />
  <ListaTarefas :kanban="kanban.done" @moveTarefa="moveTarefa" />
</template>

<style></style>
