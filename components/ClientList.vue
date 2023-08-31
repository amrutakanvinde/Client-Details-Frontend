<template>
  <div>
    <h2>Client List</h2>
    <v-list>
      <v-list-item v-for="client in clients" :key="client.id" link @click="showClientDetails(client.id)">
        <v-list-item-title>{{ client.name }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clients: []
    };
  },
  async mounted() {debugger
    const response = await this.$axios.get('/test');
    
    this.clients = response.data;
  },
  methods: {
    showClientDetails(id) {
      this.$router.push(`/clients/${id}`);
    }
  }
};
</script>
