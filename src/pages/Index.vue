<template>
  <q-page padding>
    <ul>
      <Task
         :tasks="tasks"></Task>
    </ul>
  </q-page>
</template>

<script>
import Task from '../components/Task.vue'
export default {
  data () {
    return {
      tasks: [
        {
          id: 1,
          name: 'go to shop',
          dueDate: '2019/05/02',
          dueTime: '18:38'
        },
        {
          id: 2,
          name: 'get bananas',
          dueDate: '2019/05/03',
          dueTime: '14:02'
        },
        {
          id: 3,
          name: 'get apples',
          dueDate: '2019/05/04',
          dueTime: '16:00'
        }
      ]
    }
  },
  components: {
    Task
  }
}
</script>

<style>
</style>
