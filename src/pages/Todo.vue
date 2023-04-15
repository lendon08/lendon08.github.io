<template>
  <q-page class="bg-grey-3 column">
    <q-list class="bg-white">
      <q-item
              v-for="task in tasks"
              :key="task.title"
              v-ripple>
        <q-item-section avatar>
          <q-checkbox
                      v-model="color"
                      color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Teal</q-item-label>
        </q-item-section>
      </q-item>    </q-list>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

  export default defineComponent({
    name: 'MyTodo',
    data() {
      return {
        tasks: [
          {
            title: 'Get',
            done: false
          },
          {
            title: 'Eat',
            done: false
          },
          {
            title: 'Poo',
            done: false
          },
        ]
      }

    }
  })
</script>
