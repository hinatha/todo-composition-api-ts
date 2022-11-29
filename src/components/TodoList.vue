<template>
  <div>
    <ul class="todolist">
      <!-- Display state.todoList with todo as key -->
      <li v-for="todo in state.todoList" :key="todo.todo">{{ todo.todo }}</li>
    </ul>
    <!-- TodoList component has TodoInput component inside it -->
    <Todo-input />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive} from 'vue'
import TodoInput from '../components/TodoInput.vue'


export default defineComponent({
  // Define component as TodoList
  name: 'TodoList',
  // TodoList component has TodoInput component inside it
  components: {
    TodoInput
  },

  setup() {
    // In case of lang="ts", define type inside reactive
    const state = reactive<{ todoList: [{todo: String}, {todo: String}];}>({
      // There are two temporary data
      todoList: [
          {
            todo: 'todo1',
          },
          {
            todo: 'todo2',
          }

      ]
    });
    return { state };
  }
});

</script>