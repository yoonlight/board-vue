<template>
  <v-app>
    <main-drawer :drawer.sync="drawer" />
    <main-header />
    <v-main>
      <HelloWorld />
    </v-main>
  </v-app>
</template>

<script>
import MainDrawer from "./container/MainDrawer.vue";
import MainHeader from "./container/MainHeader.vue";
import HelloWorld from "./HelloWorld";

export default {
  name: "App",

  components: {
    HelloWorld,
    MainHeader,
    MainDrawer
  },

  data: () => ({
    drawer: false
  })
};
</script>
