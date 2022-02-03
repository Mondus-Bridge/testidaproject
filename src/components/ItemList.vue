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
  max-width: 1028px;
  min-width: 320px;
  margin: 0 0 0 0;
  padding: 0;
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(332px, 1fr));
  grid-gap: 16px;
}

@media screen and (max-width: 768px) {
  .container {
    flex-wrap: wrap;
    display: flex;
    flex-direction: column;
  }
}
</style>
