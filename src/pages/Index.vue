<template>
  <q-page padding>
    <ul>
      <task
         :tasks="tasks"></task>
    </ul>
  </q-page>
</template>

<script>
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
    task: require('components/Task.vue').default
  }
}
</script>

<style>
</style>
