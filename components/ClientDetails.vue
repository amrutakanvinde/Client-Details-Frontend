<template>
  <div>
    <h2>Client Details</h2>
    <v-card>
      <v-card-title>{{ client.name }}</v-card-title>
      <v-card-text>
        <p><strong>Email:</strong> {{ client.email }}</p>
        <!-- Add more details here -->
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      client: {}
    };
  },
  async mounted() {
    const clientId = this.$route.params.id;
    const response = await this.$axios.get(`/api/clients/${clientId}`);
    this.client = response.data;
  }
};
</script>
