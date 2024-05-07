<script setup>
import MovieItem from './MovieItem.vue'
</script>

<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="item.title">
        <MovieItem :title="item.name" :stars="item.stars" @remove-movie-item="removeItem(index)" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  components: {
    MovieItem
  },
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  methods: {
    removeItem(index) {
      // Remove the item at the specified index from the items array
      this.$emit('remove-item', index)
    }
  }
}
</script>

<style scoped>
/* Add your styling here */
</style>
