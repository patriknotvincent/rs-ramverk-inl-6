<template>
  <button class="general-button" @click="handleClick">{{ buttonText }}</button>
</template>

<script>
export default {
  props: {
    buttonText: String,
  },
  methods: {
    handleClick() {
      this.$emit('button-click')
    }
  }
}
</script>

<style>
.general-button {
    padding: 10px;
    margin: 10px;
}
</style>
