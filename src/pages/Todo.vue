<template>
  <q-page class="bg-grey-3 column">
    <q-list
            class="bg-white"
            separator
            border
            >
      <q-item
              v-for="task in tasks"
              :key="task.title"
              @click="task.done = !task.done"
              :class="{'done' : task.done}"
              clickable
              v-ripple>
        <q-item-section avatar>
          <q-checkbox
                      v-model="task.done"
                      class="no-pointer-events"
                      color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
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
