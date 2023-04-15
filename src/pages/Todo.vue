<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input
               v-model="newTask"
               class="col"
               bg-color="white"
               square
               filled
               placeholder="Add Task"
               dense>

        <template v-slot:append>
          <q-btn round dense flat icon="add" />
        </template>
      </q-input>
    </div>
    <q-list
            class="bg-white"
            separator
            border
            >
      <q-item v-for="(task, index) in tasks"
              :key="task.title"
              @click="task.done = !task.done"
              :class="{'done bg-blue-1' : task.done}"
              clickable
              v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done"
                      class="no-pointer-events"
                      color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section
                        v-if="task.done"
                        side>
          <q-btn
                 @click.stop="deleteTask(index)"
                 flat
                 round
                 color="primary"
                 icon="delete" />
        </q-item-section>
      </q-item>    </q-list>
  </q-page>
</template>

<script>
  import useQuasar from 'quasar/src/composables/use-quasar.js';
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
    },
    methods: {

      deleteTask(index) {
        this.$q.dialog({
          title: 'Confirm',
          message: 'Would you like to delete?',
          cancel: true,
          persistent: true
        }).onOk(() => {
          this.$q.notify('Task Deleted')
          this.tasks.splice(index, 1)
        })

      } 
    }
  })
</script>
<style lang="scss">
  .done{
      .q-item__label{
        text-decoration: line-through;
        color:  #bbb;
      }
  }

</style>
