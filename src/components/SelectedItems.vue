<script setup>
import Item from '@/components/Item.vue';

defineProps({
  selectedItems: Array,
  title: String
})

const emit = defineEmits(['remove'])

const removeItem = (item) => {
  emit('remove', item)
}
</script>

<template>
  <div>
    <h3>{{ title }}</h3>

    <p 
      class="no-items" 
      v-if="selectedItems.length === 0 && title === 'Selected User Items'"
    >
          No items selected
    </p>
    <p 
      class="no-items" 
      v-if="selectedItems.length === 0 && title === 'Selected Choice Item'"
    >
      No item selected
    </p>

    <ul v-if="selectedItems.length">
      <Item  
        v-for="item in selectedItems" 
        :key="item.id"
        :item="item"
        @click="removeItem(item)"
      >
      </Item>
    </ul>
    
    <p
      :class="{ 'limit-selected': selectedItems.length >= 6 }" 
      v-if="selectedItems.length > 0 && title === 'Selected User Items'"
    >
        Selected: {{ selectedItems.length  }} / 6
    </p>
  </div>
</template>

<style scoped>
  .no-items {
    padding: 10px;
    color: #ff0000;
    border: 1px solid #000;
  }

  .limit-selected {
    font-weight: bold;
    color: #ff0000;
  }
</style>
