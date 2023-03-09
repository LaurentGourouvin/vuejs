<template>
  <v-list :color="color">
    <v-list-item v-for="todo in todos" :key="todo.id"
      >{{ todo.text }}
      <v-checkbox class="todos-checkbox"></v-checkbox>
    </v-list-item>
  </v-list>
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
</style>
