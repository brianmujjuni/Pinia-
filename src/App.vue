<template>
  <main>
    <header>
      <img src="./assets/pinia-logo.svg" alt="" />
      <h1>Pinia Tasks</h1>
    </header>
   
    
  </main>
</template>

<script>
import { useTaskStore } from "./stores/TaskStore";
export default {
  setup() {
    const taskStore = useTaskStore();

    return { taskStore };
  },
};
</script>
