<template>
  <div id="wrapper">
    <v-container id="container">
      <v-card id="card" elevation="12">
        <div id="card_flex">
          <v-card-title id="card_flex--title">Todolist VueJS</v-card-title>
        </div>
        <v-divider></v-divider>

        <v-toolbar title="Tâche en cours" elevation="1" color="#FFF176">Tâche en cours</v-toolbar>
        <todos-list color="#FFF9C4" :todos="todosInProgress"></todos-list>
        <v-toolbar title="Tâche terminées" elevation="1" color="#66BB6A">Tâche terminées</v-toolbar>
        <todos-list color="#A5D6A7" :todos="todosDone"></todos-list>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import { TODOS } from "./data";
import _ from "lodash";
// Import components
import TodosList from "./components/TodosList";

export default {
  name: "App",
  components: {
    TodosList,
  },
  data: () => ({
    todos: TODOS,
    todosInProgress: null,
    todosDone: null,
  }),
  methods: {
    getTodosInProgress() {
      const todosInProgress = _.cloneDeep(this.todos);
      return todosInProgress.filter((todos) => todos.status === true);
    },
    getTodosDone() {
      const todosDone = _.cloneDeep(this.todos);
      return todosDone.filter((todos) => todos.status === false);
    },
  },
  mounted() {
    this.todosInProgress = this.getTodosInProgress();
    this.todosDone = this.getTodosDone();
  },
};
</script>
<style scoped>
#wrapper {
  width: 100vw;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: cadetblue;
}
#container {
  width: 600px;
}
#card {
  min-height: 500px;
  width: 100%;
}
#card_flex {
  display: flex;
  flex-direction: column;
  margin: auto;
  width: 85%;
  gap: 0.75rem;
}
#card_flex--title {
  width: 100%;
  text-align: center;
  font-size: 24px;
  font-weight: bold;
  padding: 0.75rem 0;
  font-style: italic;
}
</style>
