<script setup>
import Item from '@/components/Item.vue';

defineProps({
  items: Array,
  title: String,
})

const emit = defineEmits(['select'])

const selectItem = (item) => {
  emit('select', item)
}
</script>

<template>
  <div>
    <h3>{{ title }}</h3>
    <ul>
      <Item  
        v-for="item in items" 
        :key="item.id"
        :item="item"
        @click="selectItem(item)" 
      />
    </ul>
  </div>
</template>