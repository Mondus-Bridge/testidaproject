<template>
  <form @submit.prevent
  novalidate="true">
    <h4>Добавление товара</h4>
    <div class="container">
      <div>
        <label 
        for=""
        class="additem__title"
            >Наименование товара</label
          >
          <span class="additem__required"></span>
        <input
          v-model="item.title"
          minlength="5"
          maxlength="25"
          type="text"
          @input="checkInput('title')"
          @blur="isLinkTouched = true"
        :class="isValidName ? 'addcard__input_error' : null"
          placeholder="Введите наименование товара"
        />
        <div v-if="isLinkError">Поле является обязательным</div>
      </div>
      <div>
         <label for="" class="additem__title"
          >Описание товара</label
        >
        <input
          v-model="item.desc"
          type="text"
          placeholder="Введите описание товара"
        />
      </div>
      <div>
        <label for=""
        class="additem__title"
        >Ссылка на изображение товара</label>
        <span class="additem__required"></span>
        <input 
        v-model="item.link" 
        type="url" 
        placeholder="Введите ссылку" 
        :class="isValidLink ? 'addcard__input_error' : null"
        @input="checkInput('link')"
        />
        <div v-if="isLinkError">Поле является обязательным</div>
      </div>
      <div>
         <label for="" class="additem__title">Цена товара</label>
         <span class="additem__required"></span>
        <input v-model="item.price" 
        :class="isValidPrice ? 'addcard__input_error' : null"
        @input="checkInput('price')" type="number" placeholder="Введите цену" />
      </div>
      <p class="addcard__error" v-if="isValidPrice">{{ errorMessage }}</p>
      <button 
      @click="addItem"
      type="submit" 
      class="additem__button"
      :disabled="!isValid">
      Добавить товар
      </button>
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
      isValidName: false,
      isValidLink: false,
      isValidPrice: false,
      errorMessage: "Поле является обязательным",
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
    checkInput(fieldName) {
      switch (fieldName) {
        case "title":
          {
            this.isValidName = this.item.title ? false : true;
          }
          break;
        case "link":
          {
            this.isValidLink = this.item.link ? false : true;
          }
          break;
        case "price":
          {
            this.isValidPrice = this.item.price ? false : true;
          }
          break;
      }
    },




  },
  computed: {
    isValid() {
      return this.item.title && this.item.link && this.item.price;
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
.add__input_error {
  outline: 1px solid rgba(255, 132, 132, 1);
}

.additem__button {
  padding: 0;
  margin: 8px 0;
  width: 100%;
  font-size: 12px;
  line-height: 15px;
  font-weight: 600;
  height: 36px;
  border: none;
  background-color: rgba(123, 174, 115, 1);
  color: rgba(255, 255, 255, 1);
  border-radius: 10px;
}
.additem__button:disabled {
  color: #b4b4b4;
  background-color: rgba(238, 238, 238, 1);
}

.additem__button:hover {
  cursor: pointer;
}

.additem__required {
  margin: 0 0 0 2px;
  display: block;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background-color: rgba(255, 132, 132, 1);
}

.additem__title {
  margin: 0 0 4px 0;
  font-size: 10px;
  font-weight: 400;
  line-height: 12px;
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
