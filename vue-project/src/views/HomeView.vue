<script setup>
import HeroImage from "../components/HeroImage.vue";
import CarSection from "../components/CarOffers.vue";
import FooterView from "../components/FooterView.vue";
</script>

<template>
  <HeroImage />

  <div class="container text-center float:right">
    <div class="d-flex flex-row flex-nowrap overflow-auto">
      <car-offers v-for="car in cars" :key="car.id" :offer="car" />
    </div>
  </div>
  <CheckOut />
  <FooterView />
</template>
<script>
export default {
  data() {
    return {
      message: "Text",
      cars: [],
    };
  },
  components: { "car-offers": CarSection },

  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const res = await fetch("cars.json");
      const val = await res.json();
      this.cars = val;
    },
  },
};
</script>
