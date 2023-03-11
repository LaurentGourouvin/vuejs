<template>
  <div id="wrapper">
    <v-container id="container">
      <v-card id="card" elevation="12">
        <div id="card_flex">
          <v-card-title id="card_flex--title">Todolist VueJS</v-card-title>
          <v-form @submit.prevent>
            <section id="formulaire">
              <v-text-field
                  type="text"
                  label="Ajouter une tâche"
                  v-model="newTodo"
                  required
              >
              </v-text-field>
              <v-btn @click="addTodos">Enregistrer</v-btn>
            </section>
          </v-form>
        </div>
        <v-divider></v-divider>

        <todos-list :todos="todos"></todos-list>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import {TODOS} from "./data";
// Import components
import TodosList from "./components/TodosList";

export default {
  name: "App",
  components: {
    TodosList,
  },
  data: () => ({
    todos: TODOS,
    newTodo: "",
    currentId: 0,
  }),
  methods: {
    addTodos() {
      if (this.newTodo === "") {
        return
      }
      this.currentId++;
      this.todos.push({id: this.currentId, text: this.newTodo, status: true, createdAt: new Date()});
      this.newTodo = "";
    },
    getMaxId() {
      let idArray = [];
      for (const todo of this.todos) {
        idArray.push(todo.id)
      }

      return Math.max(...idArray);
    },
  },

  mounted() {
    console.log("APP.VUE mounted.");
    this.currentId = this.getMaxId();
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
  font-size: 24px;
  font-weight: bold;
  font-style: italic;
}

#form {
  display: flex;
  flex-direction: row;
}

#formulaire {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: .75rem;
}

</style>
