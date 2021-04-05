<template>
  <div id="tasks">
    <TaskCard title="First Task" description="desc"></TaskCard>
    <TaskCard title="2nd Task" description="desc"></TaskCard>
    <TaskCard title="3rd Task" description="desc"></TaskCard>
  </div>
</template>

<script>
import TaskCard from './TaskCard'

export default {
  components: { TaskCard },
};
</script>

