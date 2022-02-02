<template>
  <div>
    <item-form @create="addItem" />
    <item-sort
      class="item__sort"
      v-model="selectedSort"
      :options="sortOptions"
    />
    <item-list 
    :items="sortedItems"
    @remove="removeItem" />
  </div>
</template>

<script>
import ItemForm from "./components/ItemForm.vue";
import ItemList from "./components/ItemList.vue";
import ItemSort from "./components/ItemSort.vue";
export default {
  components: {
    ItemForm,
    ItemList,
    ItemSort,
  },
  data() {
    return {
      items: [
        {
          id: 1,
          title: "Наименование товара 2",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 2000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 2,
          title: "Наименование товара 1",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 1000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 3,
          title: "Наименование товара 3",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 3000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 4,
          title: "Наименование товара 4",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 4000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 5,
          title: "Наименование товара 5",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 5000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 6,
          title: "Наименование товара 6",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 6000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 7,
          title: "Наименование товара 7",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 7000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 8,
          title: "Наименование товара 8",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 8000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
        {
          id: 9,
          title: "Наименование товара 9",
          desc: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 9000,
          link: "https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2022/01/white-polaroid-onestep-2-instant-camera-featured-image-cropped.jpg",
        },
      ],
      selectedSort: '',
      sortOptions: [
        { value: "title", name: "По наименованию" },
        { value: "price", name: "По убыванию цены" },
        { value: "price", name: "По возрастанию цены" },
      ],
    };
  },
  methods: {
    addItem(item) {
      this.items.push(item);
    },
    removeItem(item) {
      this.items = this.items.filter((i) => i.id !== item.id);
    },
  },
    computed: {
      sortedItems() {
        return [...this.items].sort((a, b) => a[this.selectedSort]?.localeCompare(b[this.selectedSort])
        )},
    },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

div {
  display: flex;
  gap: 16px;
  background: #e5e5e5;
}

.item__sort {
  width: 150px;
  height: 50px;
}
</style>
