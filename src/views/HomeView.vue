<script setup>
import { ref } from 'vue'
import ItemList from '@/components/ItemList.vue'
import SelectedItems from '@/components/SelectedItems.vue'

const userItems = [
  { id: 1, name: 'Shoes 1' },
  { id: 2, name: 'Shoes 2' },
  { id: 3, name: 'Shoes 3' },
  { id: 4, name: 'Shoes 4' },
  { id: 5, name: 'T-shirt 1' },
  { id: 6, name: 'T-shirt 2' },
  { id: 7, name: 'T-shirt 3' },
  { id: 8, name: 'T-shirt 4' }
]

const choiceItems = [
  { id: 11, name: 'Jacket 1' },
  { id: 12, name: 'Jacket 2' },
  { id: 13, name: 'Jacket 3' },
  { id: 14, name: 'Jacket 4' },
  { id: 15, name: 'Hoodie 1' },
  { id: 16, name: 'Hoodie 2' },
  { id: 17, name: 'Hoodie 3' },
  { id: 18, name: 'Hoodie 4' }
]

const selectedUserItems = ref([])
const selectedChoiceItem = ref([])

const handleUserItemSelect = (item) => {
  if (selectedUserItems.value.length < 6) {
    selectedUserItems.value.push(item)
  } else {
    alert('Вы уже выбрали 6 вещей!')
  }
}

const handleUserItemRemove = (item) => {
  if (selectedUserItems.value.length > 0) {
    selectedUserItems.value.shift(item)
  }
}

const handleChoiceItemSelect = (item) => {
  if (selectedChoiceItem.value.length === 0) {
    selectedChoiceItem.value.push(item)
  } else if (selectedChoiceItem.value[0].id !== item.id) {
    selectedChoiceItem.value[0] = item
  }
}

const handleChoiceItemRemove = (item) => {
  if (selectedChoiceItem.value.length === 1) {
    selectedChoiceItem.value.shift(item)
  }
}
</script>

<template>
  <div class="container">
    <div class="top-blocks">
      <SelectedItems 
        title="Selected User Items" 
        :selectedItems="selectedUserItems" 
        @remove="handleUserItemRemove"
      />
      <SelectedItems  
        title="Selected Choice Item" 
        :selectedItems="selectedChoiceItem" 
        @remove="handleChoiceItemRemove"
      />
    </div>

    <div class="bottom-blocks">
      <ItemList 
        title="User Items" 
        :items="userItems" 
        @select="handleUserItemSelect"
      />
      <ItemList
        title="Choice Items"
        :items="choiceItems"
        @select="handleChoiceItemSelect"
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}

.top-blocks,
.bottom-blocks {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}

h3 {
  margin: 0 0 10px;
}
</style>
