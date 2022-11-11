<template>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
</template>

<script>
import Tasks from '../components/Tasks.vue';
import AddTask from '../components/AddTask.vue';

export default {
  name: 'HomeView',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return  {
      tasks: [],
    }
  },
  methods: {
    async deleteTask(id) {
      const res = await fetch(`/api/tasks/${id}`, {method: 'DELETE'})
      res.status === 200 ? this.tasks = this.tasks.filter((item) => item.id !== id) : alert('Error deleting task')
    },
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      const updatedTask = {...taskToToggle, reminder: !taskToToggle.reminder}

      const res = await fetch(`api/tasks/${id}`, {method: 'PUT', headers: {'Content-Type': 'application/json'}, body: JSON.stringify(updatedTask)});

      const data = await res.json();
      this.tasks = this.tasks.map((item) => item.id === id ? { ...item, reminder: data.reminder } : item);
    },
    async addTask(newTask) {
      const res = await fetch('api/tasks', {
      method: 'POST', 
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(newTask)
      })
      const data = await res.json();
      console.log(data);
      this.tasks = [...this.tasks, data]

    },
    async fetchTasks() {
      const res = await fetch('api/tasks');
      const data = res.json();
      return data
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`);
      const data = res.json();
      return data
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  }, 
}
</script>
