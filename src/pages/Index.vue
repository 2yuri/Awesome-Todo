<template>
  <q-page padding>
    <ul>
      <task
        v-for="{task, index} in tasks"
        :task="task"
        :index="index"></task>
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
          name: 'go to shop',
          dueDate: '2019/05/02',
          dueTime: '18:38'
        },
        {
          name: 'get bananas',
          dueDate: '2019/05/03',
          dueTime: '14:02'
        },
        {
          name: 'get apples',
          dueDate: '2019/05/04',
          dueTime: '16:00'
        }
      ]
    }
  },
  methods: {
    deleteTask (index) {
      this.tasks.splice(index, 1)
    }
  },
  components: {
    'task' : Task
  }
}
</script>

<style>
</style>
