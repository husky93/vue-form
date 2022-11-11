<template>
  <div v-for="task in tasks" :key="task.id">
    <Task :task="task" />
  </div>
</template>

<script>
import Task from './Task.vue';

export default {
  name: 'TasksElement',
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
};
</script>
