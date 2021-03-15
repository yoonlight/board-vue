<template>
  <div>
    <v-navigation-drawer app v-model="drawer">
      <v-list nav>
        <v-sheet color="grey lighten-4" class="pa-4">
          <v-avatar class="mb-4" color="grey darken-1" size="64"></v-avatar>

          <div>john@vuetifyjs.com</div>
        </v-sheet>
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item v-for="[icon, text] in nav" :key="icon" link>
            <v-list-item-icon>
              <v-icon>{{ icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ text }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
import { EventBus } from "../../utils/eventBus";

export default {
  data: () => ({
    drawer: false,
    group: null,
    nav: [
      ["mdi-inbox-arrow-down", "Inbox"],
      ["mdi-send", "Send"],
      ["mdi-delete", "Trash"],
      ["mdi-alert-octagon", "Spam"]
    ]
  }),

  created() {
    EventBus.$on("drawer", drawer => {
      this.drawer = drawer;
    });
  }
};
</script>

<style></style>
