<template>
  <div>
    <section>
      <base-card>
        <header>
          <h2>Requests Received</h2>
        </header>
        <ul v-if="hasRequests">
          <requests-items
            v-for="req in receivedRequests"
            :key="req.id"
            :email="req.userEmail"
            :message="req.message"
          ></requests-items>
        </ul>
        <h3 v-else>You haven't received any requests yet!</h3>
      </base-card>
    </section>
  </div>
</template>
<script>
import RequestsItems from '../../components/requests/RequestsItems.vue';
export default {
  components: { RequestsItems },
  computed: {
    receivedRequests() {
      return this.$store.getters['requests/requests'];
    },
    hasRequests() {
      return this.$store.getters['requests/hasRequests'];
    },
  },
};
</script>
<style scoped>
header {
  text-align: center;
}

ul {
  list-style: none;
  margin: 2rem auto;
  padding: 0;
  max-width: 30rem;
}

h3 {
  text-align: center;
}
</style>
