<template>
  <v-list :color="color">
    <v-list-item v-for="todo in todos" :key="todo.id">{{ todo.text }}</v-list-item>
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
  mounted() {
    console.log(this.todos);
  },
};
</script>

<style scoped></style>
