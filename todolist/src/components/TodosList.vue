<template>
  <div class="todos-list">
    <v-list :color="color">
      <v-list-item v-for="todo in todos" :key="todo.id"
        >{{ todo.text }}
        <v-checkbox class="todos-checkbox"></v-checkbox>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  name: "todos-list",
  props: {
    todos: Array || null,
    color: String,
  },
  data() {
    return {};
  },
  methods: {},
  mounted() {},
};
</script>

<style scoped>
.todos-checkbox {
  position: absolute;
  right: 1rem;
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
