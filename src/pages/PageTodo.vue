<template>
<q-page class="q-pa-md">
    <NoTasks v-if="!Object.keys(tasksTodo).length" />

    <taskTodo v-if="Object.keys(tasksTodo).length" :tasksTodo="tasksTodo" />

    <tasksCompleted v-if="Object.keys(tasksCompleted).length" :tasksCompleted="tasksCompleted" />

    <div class="absolute-bottom text-center q-mb-lg">
        <q-btn round @click="showAddTask = true" color="primary" size="24px" icon="add" />
    </div>

    <q-dialog v-model="showAddTask">
        <addtask @close="showAddTask = false" />
    </q-dialog>

</q-page>
</template>

<script>
import {
    mapGetters
} from 'vuex'

export default {
    data() {
        return {
            showAddTask: false,
        }
    },
    computed: {
        ...mapGetters('tasks', ['tasksTodo', 'tasksCompleted'])
    },
    components: {
        addtask: require('components/Modals/AddTask.vue').default,
        taskTodo: require('components/Tasks/TasksTodo.vue').default,
        tasksCompleted: require('components/Tasks/TasksCompleted.vue').default,
        NoTasks: require('components/Tasks/NoTasks.vue').default
    },
    mounted() {
        this.$root.$on('ShowAddTask', () => {
            this.showAddTask = true
        })
    }
}
</script>

<style>
.text-strikethrough {
    text-decoration: line-through;
}
</style>
