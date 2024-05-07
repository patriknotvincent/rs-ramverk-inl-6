<template>
  <button @click="handleClick">{{ buttonText }}</button>
</template>

<script>
export default {
  data() {
    return {
      buttonText: 'Spara film'
    }
  },
  methods: {
    handleClick() {
        this.$emit('button-click');
    }
  }
}
</script>

<style scoped>
button {
    margin-top: 2vh;
    margin-bottom: 2vh;
}
</style>
