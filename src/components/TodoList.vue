<template>
  <div>
    <ul class="todolist">
        <!-- Display state.todoList with todo as key -->
        <li v-for="todo in state.todoList" :key="todo.todo">{{ todo.todo }}</li>
    </ul>
    <!-- add-todo is the event name of Todo-input -->
    <!-- Call addTodoAction -->
    <Todo-input @add-todo="addTodoAction" />
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
    // State receives todoList as argument and return copy of reactive state
    const state = reactive<{todoList: Array<{todo: string}>}> ({
      todoList: []
    });

    const addTodoAction = (value: string) => {
      // Push the form value to todoList
      state.todoList.push({todo: value})
    };

    return { state, addTodoAction };
  }
});
</script>