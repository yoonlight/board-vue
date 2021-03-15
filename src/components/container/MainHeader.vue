<template>
  <div>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-app-bar-nav-icon @click="drawerCtrl"></v-app-bar-nav-icon>
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>
      <v-spacer></v-spacer>
    </v-app-bar>
  </div>
</template>

<script>
import { EventBus } from "../../utils/eventBus";
export default {
  data: () => ({
    drawer: false
  }),

  methods: {
    drawerCtrl() {
      this.drawer = !this.drawer;
      EventBus.$emit("drawer", this.drawer);
    }
  }
};
</script>

<style></style>
