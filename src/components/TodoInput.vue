<template>
  <div>
    <!-- "todoRef" in v-model is synchronized with the form input value -->
    <input v-model="todoRef" type="text">
    <!-- Call add event -->
    <button @click="add">登録</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, SetupContext, ref } from 'vue'

export default defineComponent({
  // Define component as TodoInput
  name: 'TodoInput',
  // This time, context makes event by using emit
  // FYI: https://v3.ja.vuejs.org/guide/composition-api-setup.html#%E3%83%95%E3%82%9A%E3%83%AD%E3%83%8F%E3%82%9A%E3%83%86%E3%82%A3
  setup(props, context: SetupContext) {
    // Set the form value as empty by ref
    const todoRef = ref<string>('')

    // Set the event object as e to the argument
    const add = (e: any) => {
      // Change form value to todoRef.value 
      // Set this event name as 'add-todo'
      context.emit('add-todo', todoRef.value);
      // Change form value to empty
      todoRef.value = ''
    };

    return { add, todoRef };
  }
});
</script>