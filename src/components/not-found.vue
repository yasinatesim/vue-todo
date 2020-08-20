<template>
  <div v-if="items.length === 0">
    No items found.
  </div>
</template>

<script>
export default {
  name: 'NotFound',
  props: {
    items: {
      type: Array,
      required: true
    }
  }
};
</script>
