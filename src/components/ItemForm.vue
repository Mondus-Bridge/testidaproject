<template>
  <form @submit.prevent>
    <h4>Добавление товара</h4>
    <div class="container">
      <div>
        <h6>Наименование товара</h6>
        <input
          v-model="item.title"
          type="text"
          placeholder="Введите наименование товара"
        />
      </div>
      <div>
        <h6>Описание товара</h6>
        <input
          v-model="item.desc"
          type="text"
          placeholder="Введите описание товара"
        />
      </div>
      <div>
        <h6>Ссылка на изображение товара</h6>
        <input v-model="item.link" type="url" placeholder="Введите ссылку" />
      </div>
      <div>
        <h6>Цена товара</h6>
        <input v-model="item.price" type="number" placeholder="Введите цену" />
      </div>
      <button @click="addItem">Добавить товар</button>
    </div>
  </form>
</template>
<script>
export default {
  data() {
    return {
      item: {
        title: "",
        desc: "",
        price: "",
        link: "",
      },
    };
  },
  methods: {
    addItem() {
      (this.item.id = Date.now()), this.$emit("create", this.item);
      this.item = {
        title: "",
        desc: "",
        price: "",
        link: "",
      };
    },
  },
};
</script>
<style lang="scss" scoped>
.container {
  width: 400px;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 20px;
}

div {
  div {
    display: flex;
    flex-direction: column;
    background: #fffefb;
    position: relative;
  }
  input {
    background: #fffefb;
    box-sizing: border-box;
    border: solid #fffefb 1px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
  }
  button {
    background: #eeeeee;
    border-radius: 10px;
    width: auto;
    height: 36px;
  }
}
</style>
