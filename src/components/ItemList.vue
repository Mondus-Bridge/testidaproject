<template lang="">
  <div class="container" v-show="items.length > 0">
    <item-item
      v-for="item in items"
      :item="item"
      :key="item.id"
      @remove="$emit('remove', item)"
    />
  </div>
  <h2 v-show="items.length === 0">Товаров не найдено</h2>
</template>
<script>
import ItemItem from "@/components/ItemItem";
export default {
  components: { ItemItem },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  position: relative;
}
</style>
