<template>
  <div id="app">
    <Tasks :tasks="tasks" v-on:deleteTaskEvent="RemoveTask" v-on:completeTaskEvent="completeTask"></Tasks>

    <input type="text" v-model="newTask" class="form-control mb-2" @keyup.enter="addNewTask">
    
    <button @click.prevent="addNewTask" class="btn btn-success btn-block">Add New Task</button>
  </div>
</template>



<script>
import Tasks from "@/components/Tasks.vue";

export default {
  name: "app",
  components: {
    Tasks
  },
  data() {
    return {
      newTask: null,
      tasks: [
        {
          body: " Go to school",
          completed: true
        },
        {
          body: " Go to schop",
          completed: false
        },
        {
          body: " Go to bed",
          completed: false
        }
      ]
    };
  },
  methods: {
    addNewTask() {
      this.tasks.push({
        body: this.newTask,
        completed: false
      });
      this.newTask = null;
    },

    RemoveTask(index) {
      this.tasks.splice(index, 1);
    },
    completeTask(task) {
      task.completed = !task.completed;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #151616;
  margin-top: 60px;
}

.card {
  padding: 20px;
  background: #eee;
}
</style>