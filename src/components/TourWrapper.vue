<template>
  <ul v-if="tourData.length > 0">
    <TourCard v-for="tour in tourData" :key="tour.id" :tour="tour" />
  </ul>
</template>

<script>
import TourCard from './TourCard.vue'
export default {
  components: { TourCard },
  data() {
    return {
      url: 'https://raw.githubusercontent.com/hexschool/js-training/main/travelAPI-lv1.json',
      tourData: []
    }
  },
  methods: {
    async getTourData() {
      const res = await fetch(this.url)
      this.tourData = await res.json()
    }
  },
  mounted() {
    this.getTourData()
  }
}
</script>

<style scoped>
ul {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  max-width: 1280px;
  justify-content: center;
  margin: 0 auto;
  list-style-type: none;
}
@media (max-width: 768px) {
  ul {
    flex-wrap: wrap;
    padding: 0;
  }
}
</style>
