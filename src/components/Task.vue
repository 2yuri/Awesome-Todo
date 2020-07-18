<template>
    <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <div>{{ task.name }} {{ index }}</div>
      <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'task',
  props: ['tasks'],
  methods: {
    deleteTask (index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>
