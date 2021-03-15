<template>
  <v-app>
    <main-drawer :drawer.sync="drawer" />
    <main-header />
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
import MainDrawer from "./container/MainDrawer.vue";
import MainHeader from "./container/MainHeader.vue";

export default {
  name: "App",

  components: {
    MainHeader,
    MainDrawer
  },

  data: () => ({
    drawer: false
  })
};
</script>
