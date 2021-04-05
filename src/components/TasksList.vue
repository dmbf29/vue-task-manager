<template>
  <div id="tasks">
    <button
      class="btn round-icon"
      @click="addTask(newTitle, newDescription), resetForm()">+</button>

    <div class="task-card new-task">
      <div>
        <input
          type="text"
          placeholder="What would you like to do?"
          v-model="newTitle"
        />
        <textarea
          placeholder="Add some details about your task..."
          v-model="newDescription"
        ></textarea>
      </div>
    </div>

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
      newTitle: '',
      newDescription: ''
    };
  },

  methods: {
    addTask(title, description, done = false) {
      this.tasks.unshift({ title, description, done})
    },
    resetForm() {
      this.newTitle = ""
      this.newDescription = ""
    }
  }
}
</script>

<style lang="scss">
@keyframes expand-vertical { from { min-height: 0; height: 0; } to { min-height: 6rem; } }
.task-card.new-task {
  animation: expand-vertical 0.2s;
  overflow: hidden;
  background-color: white;
  border-left: solid 5px #35495e;
  &, &:hover { transform: scale(1.1); box-shadow: 2px 3px 10px rgba(black, 0.2); }
  & + .tasks-list { pointer-events: none; }
  input { font-size: 1.17rem; font-weight: bold; width: 100%; }
  textarea { width: 100%; font-size: 0.9rem; resize: none; }
}
</style>

