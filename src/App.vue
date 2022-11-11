<template>
  <div class="container">
    <Header title="Hello!" />
    <AddTask @add-task="addTask" />
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((item) => item.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((item) => item.id === id ? { ...item, reminder: !item.reminder } : item);
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask]
    }
  },
  created() {
    this.tasks = [{
      id: 1,
      text: 'Doctors Appintment',
      day: 'March 1st at 2:30pm',
      reminder: true,
    },
    {
      id: 2,
      text: 'Doctors Appintment',
      day: 'March 1st at 2:30pm',
      reminder: false,
    },
    {
      id: 3,
      text: 'Doctors Appintment',
      day: 'March 1st at 2:30pm',
      reminder: true,
    }];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
