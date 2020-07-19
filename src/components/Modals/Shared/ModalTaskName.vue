<template>
    <div class="row q-mb-sm">
          <q-input
            :rules="[val => !!val || 'Field is required']"
            outlined
            autofocus
            :value="name"
            @input="$emit('update:name', $event)"
            ref="name"
            class="col"
            label="Task name"
          >
            <template v-slot:append>
              <q-icon v-if="name" name="close" @click="$emit('update:name', '')" class="cursor-pointer" />
            </template>          
          </q-input>
    </div>
</template>

<script>
export default {
  props: ['name']
}
</script>