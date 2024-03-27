<template>
  <div>
    <section>
      <base-card>
        <h2>{{ fullName }}</h2>
        <h3>${{ rate }}/hour</h3>
      </base-card>
    </section>
    <section>
      <base-card>
        <header>
          <h2>Interested Reach out now</h2>
          <base-button link:to="contactLink"> Contact </base-button>
        </header>
        <router-view></router-view>
      </base-card>
    </section>
    <section>
      <BaseCard>
        <base-badge
          v-for="area in areas"
          :key="area"
          :type="area"
          :title="area"
        ></base-badge>
        <p>{{ description }}</p>
      </BaseCard>
    </section>
  </div>
</template>
<script>
import BaseBadge from '../../components/ui/BaseBadge.vue';
import BaseButton from '../../components/ui/BaseButton.vue';
import BaseCard from '../../components/ui/BaseCard.vue';
export default {
  props: ['id'],
  data() {
    return {
      selectedCoach: null,
    };
  },
  computed: {
    areas() {
      return this.selectedCoach.areas;
    },
    rate() {
      return this.selectedCoach.hourlyRate;
    },
    description() {
      return this.selectedCoach.description;
    },
    fullName() {
      return this.selectedCoach.firstName + '' + this.selectedCoach.lastName;
    },
    contactLink() {
      return this.$route.path + '/' + this.id + '/contact';
    },
  },
  created() {
    this.selectedCoach = this.$store.getters['coaches/coaches'].find(
      (coach) => coach.id == this.id
    );
    // console.log(this.contactLink);
  },
  components: { BaseCard, BaseButton, BaseBadge },
};
</script>
