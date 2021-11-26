<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="glossy">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />

        <q-toolbar-title>
          Решение задач симплекс методом
        </q-toolbar-title>

        <div><a href="https://github.com/RusAl84/simplex_quasar" >github.com/RusAl84/simplex_quasar</a></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-grey-2"
    >
      <q-list>
        <q-item-label header>Essential Links</q-item-label>
        <q-item clickable tag="a" href="/">
          <q-item-section avatar>
            <q-icon name="school" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Главная</q-item-label>
<!--            <q-item-label caption>страница</q-item-label>-->
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" href="/about">
          <q-item-section avatar>
            <q-icon name="code" />
          </q-item-section>
          <q-item-section>
            <q-item-label>О проекте</q-item-label>
<!--            <q-item-label caption>решение задач симплекс методом</q-item-label>-->
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
<!--      <HelloWorld />-->
      <router-view></router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'LayoutDefault',

  components: {
    // HelloWorld
  },

  setup () {
    return {
      leftDrawerOpen: ref(false)
    }
  }
}
</script>
