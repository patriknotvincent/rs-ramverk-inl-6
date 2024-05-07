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
import MovieItem from './MovieItem.vue';

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
};
</script>

<style scoped>
 ul {
    padding:0;
    list-style-type: none;
 }
</style>
