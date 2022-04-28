<script>
export default {
  props: ["kanban"],

  mounted() {},
};
</script>

<template>
  <div class="listaKanban">
    <div class="titulo tituloPrincipal">
      <h3>{{ kanban.titulo }}</h3>
    </div>
    <ul>
      <li v-for="tarefa in kanban.itens" :key="tarefa.id">
        <div class="titulo">{{ tarefa.titulo }}</div>
        <div>Conteudo</div>
        <div class="btns">
          <input
            v-if="kanban.kanbanNext"
            type="button"
            value="next"
            @click="$emit('moveTarefa', kanban.name, kanban.kanbanNext, tarefa)"
          />
          <input
            v-if="kanban.kanbanBack"
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

.tituloPrincipal {
  background-color: darkblue;
  color: white;
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

.btns {
  justify-content: end;
  display: flex;
  flex-direction: row;
}
</style>
