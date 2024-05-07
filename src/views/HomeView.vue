<script setup>
import HeaderItem from '@/components/HeaderItem.vue'
import InputForm from '@/components/InputForm.vue'
import GeneralButton from '@/components/GeneralButton.vue'
import InputButton from '@/components/InputButton.vue'
import ItemList from '@/components/ItemList.vue'
</script>

<template>
  <main>
    <HeaderItem></HeaderItem>
    <InputForm
      :titleValue="titleData"
      :ratingValue="ratingData"
      @title-change="updateTitleData"
      @rating-change="updateRatingData">
    </InputForm>
    <InputButton @button-click="handleButtonClick"></InputButton>
    <ItemList :items="itemsData" @remove-item="removeItemFromList"></ItemList>
    <GeneralButton @button-click="sortListAlphabetic" :buttonText="'Sortera Alfabetiskt'"></GeneralButton>
    <GeneralButton @button-click="sortListStarNumeric" :buttonText="'Sortera På Stjärnor'"></GeneralButton>
  </main>
</template>

<script>
export default {
  components: {
    HeaderItem,
    InputForm,
    InputButton,
    ItemList,
    GeneralButton
  },
  data() {
    return {
      itemsData: [
        { name: 'Item 1', stars: '1' },
        { name: 'Item 2', stars: '2' },
        { name: 'Item 3', stars: '3' }
      ],
      titleData: '',
      ratingData: '',
      formValidated: false
    }
  },
  methods: {
    updateTitleData(title) {
      this.titleData = title
    },
    updateRatingData(rating) {
      this.ratingData = rating
    },
    handleButtonClick() {
      if (this.titleData === '') {
        alert('Fyll i film')
        return
      }
      if (this.ratingData === '') {
        alert('Fyll i antal stjärnor')
        return
      }
      this.addItemToList()
      this.resetInputFields()
    },
    addItemToList() {
      const newItem = {
        name: this.titleData,
        stars: this.ratingData
      }
      this.itemsData.push(newItem)
    },
    resetInputFields() {
      this.titleData = ''
      this.ratingData = ''
      this.formValidated = false
    },
    removeItemFromList(index) {
      this.itemsData.splice(index, 1)
    },
    sortListAlphabetic() {
      console.log("BEFORE: ",this.itemsData)
      this.itemsData.sort((a, b) => a.name.localeCompare(b.name));
      console.log("AFTER: ",this.itemsData)
    },
    sortListStarNumeric() {
      console.log("BEFORE: ", this.itemsData)
      this.itemsData.sort((a, b) => parseInt(a.stars) - parseInt(b.stars));
      console.log("AFTER: ", this.itemsData)
    }
  }
}
</script>

<style scoped>
</style>
