<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <a class="title" @click.prevent="$router.push('/')">4択クイズアプリ</a>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <router-view :key="$route.fullPath" />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'App',

  components: {

  },

  data: () => ({
    //
  })
})
</script>

<style scoped>
.title {
  color: white;
}
</style>