<template>
<q-card>

    <modalHeader>
        <slot></slot>
    </modalHeader>

    <form @submit.prevent="submitForm">
        <q-card-section>
            <modalTaskName ref="modalTaskName" :name.sync="taskToSubmit.name" />
            <modalDueDate @clear="clearDueDate" :dueDate.sync="taskToSubmit.dueDate" />
            <modalDueTime v-if="taskToSubmit.dueDate" :dueTime.sync="taskToSubmit.dueTime" />
        </q-card-section>

        <modalButtons></modalButtons>

    </form>
</q-card>
</template>

<script>
import {
    mapActions
} from 'vuex'

export default {
    data() {
        return {
            taskToSubmit: {
                name: "",
                dueDate: "",
                dueTime: "",
                completed: false
            }
        };
    },
    methods: {
        ...mapActions('tasks', ['addTask']),
        submitForm() {
            this.$refs.modalTaskName.$refs.name.validate()
            if (!this.$refs.modalTaskName.$refs.name.hasError) {
                this.submitTask()
            }
        },
        submitTask() {
            this.addTask(this.taskToSubmit)
            this.$emit('close')
        },
        clearDueDate() {
            this.taskToSubmit.dueDate = ''
            this.taskToSubmit.dueTime = ''
        }
    },
    components: {
        modalHeader: require('components/Modals/Shared/ModalHeader.vue').default,
        modalTaskName: require('components/Modals/Shared/ModalTaskName.vue').default,
        modalDueDate: require('components/Modals/Shared/ModalDueDate.vue').default,
        modalDueTime: require('components/Modals/Shared/modalDueTime.vue').default,
        modalButtons: require('components/Modals/Shared/modalButtons.vue').default

    }
};
</script>
