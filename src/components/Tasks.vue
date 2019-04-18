<template>
  <div class="mb-1 text-left">
    <div class="card">
      <ul class="list-group">
        <div v-for="(task,index) in tasks" :key="index">
          <li class="list-group-item">
            <div :class="task.completed ? 'completed' : '' ">{{task.body}}</div>

            <div class="icons">
              <i @click.prevent="completeTask(task)" class="fas fa-check-circle"></i>
              <i @click.prevent="deleteTask(index)" class="fas fa-trash-alt ml-3"></i>
            </div>
          </li>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tasks: null
  },
  methods: {
    completeTask(task) {
      //this.task.completed = !this.task.completed
      this.$emit("completeTaskEvent", task);
    },
    deleteTask(index) {
      //send event to main app
      this.$emit("deleteTaskEvent", index);
    }
  }
};
</script>

<style scoped>
.completed {
  color: green;
  text-decoration: line-through;
}
.list-group-item {
  display: flex;
  justify-content: space-between;
}
</style>
