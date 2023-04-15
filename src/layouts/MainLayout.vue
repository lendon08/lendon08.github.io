<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn flat
               dense
               round
               icon="menu"
               aria-label="Menu"
               @click="toggleLeftDrawer" />
      </q-toolbar>
      <div class="q-px-lg q-px-xl q-mb-md">
        <div class="text-h3">To-Do</div>
        <div class="text-subtitle1">{{todaysDate}}</div>
      </div>
      <q-img src="../assets/mountains.jpg"
             class="header-image absolute-top" />
    </q-header>

    <q-drawer v-model="leftDrawerOpen"
              show-if-above
              :width="250"
              :breakpoint="600">
      <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
        <q-list padding>
          <q-item
                  to="/"
                  exact
                  clickable
                  v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section>
              Todo
            </q-item-section>
          </q-item>
          <q-item
                  to="/help"
                  exact
                  clickable
                  v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section>
              Help
            </q-item-section>
          </q-item>

        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="../assets/mountains.jpg" style="height: 192px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="../assets/avatar.png">
          </q-avatar>
          <div class="text-weight-bold">Lendon Ato</div>
          <div>@Atolendon</div>
        </div>
      </q-img>
    </q-drawer>


    <q-page-container>
      <router-view v-slot="{ Component }">
      <keep-alive>
        <component :is="Component" />
      </keep-alive>
      </router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
  import { date } from 'quasar'

  
import { defineComponent, ref } from 'vue'


export default defineComponent({
  name: 'MainLayout',


  setup () {
    const leftDrawerOpen = ref(false)
    const timeStamp = Date.now()
    const todaysDate = date.formatDate(timeStamp, 'dddd d MMMM')
    return {
      todaysDate,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
<style class="scss">
  .header-image{
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter:grayscale(100%);
  }

</style>
