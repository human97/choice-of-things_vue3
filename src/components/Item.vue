<script setup>
defineProps({
  item: {
    type: Object,
    required: true,
    default: () => ({})
  }
})

</script>

<template>
  <li>
    {{ item.name }}
  </li>
</template>