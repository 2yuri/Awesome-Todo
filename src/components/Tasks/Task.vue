<template>
  <q-item
    @click="updateTasks({ id: id, updates: { completed: !task.completed } })"
    clickable
    v-ripple
    :class="!task.completed ? 'bg-orange-1' : 'bg-green-1'"
  >
    <q-item-section side top>
      <q-checkbox v-model="task.completed" />
    </q-item-section>

    <q-item-section>
      <q-item-label :class="{ 'text-strikethrough': task.completed }">
        {{ task.name }}
      </q-item-label>
    </q-item-section>

    <q-item-section 
     side
     v-if="task.dueDate"
    >
      <div class="row">
        <div class="column justify-center">
          <q-icon class="q-mr-xs" name="event" size="18px" />
        </div>
        <div class="column">
          <q-item-label caption class="row justify-end">
            {{ task.dueDate }}
          </q-item-label>
          <q-item-label caption class="row justify-end">
            <small>{{ task.dueTime }}</small>
          </q-item-label>
        </div>
      </div>
    </q-item-section>

    <q-item-section side>
      <div class="row">
          <q-btn
       @click.stop="showEditTask = true"
       flat
       round
       color="primary"
       icon="edit"
       dense
      />
      <q-btn
       @click.stop="promptToDelete(id)"
       flat
       round
       color="red"
       icon="delete"
       dense
      />
      </div>
      
    </q-item-section>

    <q-dialog v-model="showEditTask">
      <edittask :task="task" :id="id" @close="showEditTask = false" />
    </q-dialog>

  </q-item>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  props: ['task', 'id'],
  data () {
    return {
      showEditTask: false
    }
  },
  methods: {
    ...mapActions('tasks', ['updateTasks', 'deleteTask']),
    promptToDelete(id) {
      this.$q.dialog({
        title: 'Confirm',
        message: 'Really delete?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.deleteTask(id)
      })
    }
  },
  components: {
    edittask: require('components/Modals/EditTask.vue').default
  }
}
</script>
