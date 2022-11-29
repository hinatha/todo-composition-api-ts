<template>
  <!-- Component of TodoList -->
  <TodoList />
</template>

<script lang="ts">
import TodoList from './components/TodoList.vue'

export default {
  // Appears as <App>
  // FYI: https://prograshi.com/language/vue-js/purpose-of-name-in-export-default/
  name: 'App', 
  components: {
    TodoList // Set TodoList as components
  }
}
</script>