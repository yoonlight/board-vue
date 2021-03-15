<template>
  <div>
    <v-navigation-drawer app v-model="drawer">
      <v-list nav>
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-title>Foo</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Bar</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Fizz</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Buzz</v-list-item-title>
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
    group: null
  }),

  created() {
    EventBus.$on("drawer", drawer => {
      this.drawer = drawer;
    });
  }
};
</script>

<style></style>
