<template>
  <q-page class="q-pa-md">
    <q-list
     v-if="Object.keys(tasks).length"
     bordered
     separator
    >

      <task
       v-for="(task, key) in tasks"
       :key="key"
       :task="task"
       :id="key"
      ></task>

    </q-list>

    <div class="absolute-bottom text-center q-mb-lg">
      <q-btn
        round
        @click="showAddTask = true"
        color="primary"
        size="24px"
        icon="add"
      />
    </div>

    <q-dialog v-model="showAddTask">
      <addtask @close="showAddTask = false" />
    </q-dialog>

  </q-page>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  data () {
    return {
      showAddTask: false,
    }
  },
  computed: {
    ...mapGetters('tasks', ['tasks'])
  },
  components: {
    task: require('components/Tasks/Task.vue').default,
    addtask: require('components/Modals/AddTask.vue').default
  }
}
</script>

<style>
  .text-strikethrough {
    text-decoration: line-through;
  }
</style>
