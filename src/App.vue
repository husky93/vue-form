<template>
  <div class="container">
    <Header title="Hello!" />
    <Tasks :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
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
