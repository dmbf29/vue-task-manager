<template>
  <div id="tasks">
    <button
      class="btn round-icon"
      @click="addTask('My new task', 'My new description')">+</button>

    <div v-if="tasks.length > 0">
      <TaskCard
        v-for="(task, index) in tasks"
        :key="index"
        :title="task.title"
        :description="task.description"
        :done="task.done">
      </TaskCard>
    </div>

    <p v-else>You don't have any tasks yet 😢</p>
  </div>
</template>

<script>
import TaskCard from './TaskCard'

export default {
  components: { TaskCard },


  data() {
    return {
      tasks: [],
    };
  },

  methods: {
    addTask(title, description, done = false) {
      this.tasks.unshift({ title, description, done})
    }
  }
}
</script>

