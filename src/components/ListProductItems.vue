<script setup>
import ProductItem from '@/components/ProductItem.vue';

defineProps({
  products: Array,
  title: String,
})

const emit = defineEmits(['select'])

const selectItem = (product) => {
  emit('select', product)
}
</script>

<template>
  <div>
    <h3>{{ title }}</h3>
    <div class="list">
      <ProductItem  
        v-for="product in products" 
        :key="product.id"
        :product="product"
        @click="selectItem(product)" 
      />
    </div>
  </div>
</template>