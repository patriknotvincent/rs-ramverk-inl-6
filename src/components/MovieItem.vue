<script setup>
import StarItem from './StarItem.vue'
</script>

<template>
  <div class="container">
    <span>{{ title }}</span>
    <div class="star-container">
      <StarItem v-for="index in parseInt(stars)" :key="index" />
      <button @click="removeMovieItem">Ta Bort</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    stars: {
      type: String
    }
  },
  methods: {
    removeMovieItem() {
      this.$emit('remove-movie-item', this)
    }
  },
  components: {
    StarItem
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
}
.star-container {
  display: flex;
}
</style>
