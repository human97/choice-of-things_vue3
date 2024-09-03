<script setup>
defineProps({
  product: {
    type: Object,
    required: true,
    default: () => ({})
  }
})
</script>

<template>
  <div class="item">
    {{ product.name }}
  </div>
</template>

<style lang="scss" scoped>
.item {
  padding: 5px;
  border: 1px solid var(--vt-c-divider-light-2);
  border-radius: 10px;
  cursor: pointer;

  &:hover {
    background-color: var(--vt-c-white-mute);
  }
}
</style>