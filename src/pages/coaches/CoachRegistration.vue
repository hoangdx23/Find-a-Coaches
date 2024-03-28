<template>
  <div>
    <section>
      <base-card>
        <h2>Register as a coach now!</h2>
        <coach-from @save-data="saveData"></coach-from>
      </base-card>
    </section>
  </div>
</template>
<script>
import CoachFrom from '../../components/coaches/CoachFrom.vue';
export default {
  components: { CoachFrom },
  methods: {
    saveData(data) {
      this.$store.dispatch('coaches/registerCoach', data);
      this.$router.replace('/coaches');
    },
  },
};
</script>
