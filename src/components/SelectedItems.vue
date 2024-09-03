<script setup>
import ProductItem from '@/components/ProductItem.vue';
import AppButton from '@/components/UI/AppButton.vue';


defineProps({
  selectedItems: Array,
  title: String
})

const emit = defineEmits(['remove', 'clear'])

const removeItem = (product) => {
  emit('remove', product)
}

const clearSelectedList = () => {
  emit('clear')
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

    <div  
      v-if="selectedItems.length"
      class="list"
    >
      <ProductItem  
        v-for="product in selectedItems" 
        :key="product.id"
        :product="product"
        @click="removeItem(product)"
      />
    </div>
    
    <div>
      <p
        :class="{ 'limit-selected': selectedItems.length >= 6 }" 
        v-if="selectedItems.length > 0 && title === 'Selected User Items'"
      >
        Selected: {{ selectedItems.length  }} / 6
      </p>

      <AppButton 
        v-if="selectedItems.length > 1 && title === 'Selected User Items'"
        label="Clear Selected List"
        color="warning"
        size="small" 
        outlined
        @click="clearSelectedList"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .no-items {
    padding: 10px;
    text-align: center;
    color: var(--danger);
    border: 1px solid var(--vt-c-divider-dark-2);
    border-radius: 10px;
  }

  .limit-selected {
    font-weight: bold;
    color: var(--danger);
  }
</style>
