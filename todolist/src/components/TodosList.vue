<template>
  <div class="todolist">
    <v-toolbar title="Tâche en cours" elevation="1" color="#FFF176">
      Tâche en cours
    </v-toolbar>

    <div class="todos-list">
      <v-list :color="color">
        <v-list-item class="list-hover" v-for="(todo, index) in todosInProgress" :key="todo.id"
        >{{ todo.text }}
          <v-btn class="todos-btn" color="#EF5350" @click="setTodoDone(index)" small>Terminé</v-btn>
        </v-list-item>
      </v-list>
    </div>


    <v-toolbar title="Tâche terminées" elevation="1" color="#66BB6A">
      Tâche terminées
    </v-toolbar>
    <div class="todos-list">
      <v-list :color="color">
        <v-list-item class="list-hover" v-for="(todo,index) in todosDone" :key="todo.id"
        >{{ todo.text }}
          <v-btn class="todos-btn" color="#388E3C" @click="setTodoInProgress(index)" small>Ré-activer</v-btn>
        </v-list-item>
      </v-list>
    </div>
  </div>
</template>

<script>
export default {
  name: "todos-list",
  props: {
    todos: Array || null,
    newTodo: String,
    color: String,
  },
  data() {
    return {
      todosDone: [],
      todosInProgress: [],
    };
  },
  watch: {
    // Je surveille le changement de ma todosList
    todos: {
      handler(){
        this.todosInProgress = this.filteredTodo(this.todos,true);
        this.todosDone = this.filteredTodo(this.todos, false);
      },
      deep: true
    },
  },
  methods: {
    setTodoDone(index){
      this.todosInProgress[index].status = !this.todosInProgress[index].status;
    },
    setTodoInProgress(index){
      this.todosDone[index].status = !this.todosDone[index].status;
    },
    filteredTodo(list, status){
      return list
          .filter((data) => data.status === status)
          .sort((currentTodo, nextTodo)=>{
            return nextTodo.createdAt - currentTodo.createdAt
          })
    }
  },
  mounted() {
    console.log("TodoList mounted");
    this.todosInProgress = this.filteredTodo(this.todos, true);
    this.todosDone = this.filteredTodo(this.todos, false);
  },
};
</script>

<style scoped>
.todos-btn {
  position: absolute;
  right: 1rem;
  color: white;
}
.list-hover:hover {
  background: #ECEFF1;
}

.todos-list {
  max-height: 200px;
  overflow-y: auto;
}

/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #888;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
