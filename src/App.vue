<template>
  <div class="bg-dark">
    <AppHeader></AppHeader>
    <router-view></router-view>
    <AppFooter></AppFooter>
  </div>
</template>

<script>
import axios from 'axios';
import { store } from './store.js';
import AppHeader from './components/AppHeader.vue';
import AppFooter from './components/AppFooter.vue';
export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter
  },
  data() {
    return {
      store,
    }
  },
  methods: {

  },
  mounted() {
  }
}
</script>

<style lang="scss" scoped>
@use './assets/styles/partials/variables' as *;
</style>