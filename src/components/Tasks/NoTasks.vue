<template>
      <q-banner dense class="bg-orange-1">
      <template v-slot:avatar>
        <q-icon name="check" color="primary" />
      </template>
      No tasks to do today!
      <template v-slot:action>
        <q-btn @click="$root.$emit('ShowAddTask')" flat color="primary" label="Add Task" />
      </template>
    </q-banner>
</template>

<script>
export default {

}
</script>

<style>

</style>