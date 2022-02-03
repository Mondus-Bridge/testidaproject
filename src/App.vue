<template>
  <div class="container">
    <div class="app__block">
      <div><h2>Добавление товара</h2></div>
      <div>
        <item-sort
          class="item__sort"
          v-model="selectedSort"
          :options="sortOptions"
        />
      </div>
    </div>

    <div class="app__list">
      <div><item-form class="app__form" @create="addItem" /></div>
      <div><item-list :items="sortedItems" @remove="removeItem" /></div>
    </div>
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
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "По наименованию" },
        { value: "priceToMin", name: "По убыванию цены" },
        { value: "priceToMax", name: "По возрастанию цены" },
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
      switch (this.selectedSort) {
        case "title": {
          return [...this.items].sort((a, b) =>
            a[this.selectedSort]?.localeCompare(b[this.selectedSort])
          );
        }
        case "priceToMin": {
          return [...this.items].sort((a, b) => b.price - a.price);
        }
        case "priceToMax": {
          return [...this.items].sort((a, b) => a.price - b.price);
        }

        default: {
          return this.items;
        }
      }
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: rgba(255, 254, 251, 0.8);
}

.container {
  display: flex;
  flex-direction: column;
}

.app__block {
  display: flex;
  justify-content: space-between;
  margin: 0 230px 16px 275px;
  font-weight: 400;
  font-size: 20px;
  line-height: 42px;
  color: #3f3f3f;
}

.app__list {
  display: flex;
  justify-content: center;
  box-sizing: border-box;
  gap: 16px;
}

.item__sort {
  width: auto;
  padding: 10px 16px;
  background-color: #fffefb;
  border: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  font-size: 12px;
  font-weight: 400;
  color: #b4b4b4;
  background-position: center right 16px;
  border-radius: 4px;
  box-sizing: border-box;
  appearance: none;
  cursor: pointer;
}

@media screen and (max-width: 768px) {
  .app__list {
    flex-wrap: wrap;
  }
}
</style>
