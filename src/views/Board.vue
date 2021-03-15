<template>
  <div>
    <v-container class="py-8 px-6" fluid>
      <v-card>
        <v-list two-line>
          <template v-for="item in items">
            <v-list-item :key="item.id">
              <v-list-item-avatar color="grey darken-1"> </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title>{{ item.title }}</v-list-item-title>

                <v-list-item-subtitle>
                  {{ item.body }}
                </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-divider
              v-if="item.id !== 6"
              :key="`divider-${item.id}`"
              inset
            ></v-divider>
          </template>
        </v-list>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  async created() {
    await this.getTodo(this.offset, this.limit);
    console.log(this.items);
    console.log(this.pagination);
  },

  data: () => ({
    drawer: null,
    items: [],
    offset: 1,
    limit: 10,
    pagination: 1
  }),

  methods: {
    getTodo: async function(offset, limit) {
      const data = await this.axios
        .get(`api/board?offset=${offset}&limit=${limit}`)
        .then(result => result.data);
      this.items = data.query;
      this.pagination = data.pagination;
    },

    deleteTodo: async function(id) {
      await this.axios
        .delete(`api/board/${id}`)
        .then(result =>
          this.$toasted.success(result.data.message, { duration: 2000 })
        );
      await this.getTodo(this.offset, this.limit);
      this.deleteDialog = false;
    },

    updateTodo: async function(val) {
      await this.axios.put(`api/board/${val._id}`, val).then(result => {
        console.log(result);
        this.$toasted.success(result.data.message, { duration: 2000 });
        this.dialog = false;
      });
      await this.getTodo(this.offset, this.limit);
    },

    addTodo: async function(val) {
      if (this.$refs.form.validate()) {
        await this.axios
          .post(`api/board`, val)
          .then(result =>
            this.$toasted.success(result.data, { duration: 2000 })
          );
        await this.getTodo(this.offset, this.limit);
        this.$refs.form.reset();
      }
    }
  }
};
</script>

<style></style>
