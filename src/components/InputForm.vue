<template>
  <div class="form">
    <label>{{ titleFieldLabel }}</label>
    <input v-model="titleInputValue" type="text" @input="handleTitleInput" required />
    <label>{{ ratingInputLabel }}</label>
    <select v-model="ratingInputValue" @change="handleRatingChange" required>
      <option disabled value="">{{ 'Välj betyg här...' }}</option>
      <option>1</option>
      <option>2</option>
      <option>3</option>
      <option>4</option>
      <option>5</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    titleValue: String,
    ratingValue: String,
    formValidated: String
  },
  data() {
    return {
      titleInputValue: this.titleValue,
      titleFieldLabel: 'Titel',
      ratingInputValue: this.ratingValue,
      ratingInputLabel: 'Betyg',
      validateForm: this.formValidated
    }
  },
  methods: {
    handleTitleInput() {
      this.$emit('title-change', this.titleInputValue)
      this.isFormValidated()
    },
    handleRatingChange() {
      this.$emit('rating-change', this.ratingInputValue)
      this.isFormValidated()
    },
    isFormValidated() {
      this.formValid = this.titleInputValue.trim() !== '' && this.ratingInputValue !== ''
    }
  },
  watch: {
    titleValue(value) {
      this.titleInputValue = value
    },
    ratingValue(value) {
      this.ratingInputValue = value
    },
    validityValue(value) {
      this.isFormValidated = value
    }
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
}

input {
  margin-bottom: 1vh;
}
</style>
