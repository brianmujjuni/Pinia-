<template>
  <main>
    <header>
      <img src="./assets/pinia-logo.svg" alt="" />
      <h1>Pinia Tasks</h1>
    </header>
    <div class="new-task-form">
      <TaskForm/>
    </div>
   <!--filter-->
    <nav class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Fav tasks</button>
    </nav>
    <!--loading-->
    <div class="loading" v-if="taskStore.isLoading">loading tasks </div>

    <div class="task-list" v-if="filter  === 'all'">
      <p>you have {{ taskStore.totalCount }} tasks</p>
      <div v-for="task in taskStore.tasks">
        <TaskDetails :task="task"/> 
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <p>favorites</p>
      <div v-for="task in taskStore.favs">
        <TaskDetails :task="task"/> 
      </div>
    </div>
    

  </main>
</template>

<script>
import { ref } from "vue";
import TaskDetails from "./components/TaskDetails.vue";
import TaskForm from "./components/TaskForm.vue";
import { useTaskStore } from "./stores/TaskStore";
export default {
  components:{ TaskDetails, TaskForm },
  setup() {
    
    const taskStore = useTaskStore();
    
    //fetch tasks
    taskStore.getTasks()

    const filter = ref('all')
    return { taskStore,filter };
  },
};
</script>
