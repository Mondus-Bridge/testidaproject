<template>
  <div class="additem">
  <form 
      class="additem__form"
      @submit.prevent novalidate="true">
      <div class="additem__block">
        <div class="additem__label">
          <label for="" class="additem__title">Наименование товара</label>
          <span class="additem__required"></span>
        </div>
        <input
          v-model="item.title"
          minlength="5"
          maxlength="25"
          type="text"
          @input="checkInput('title')"
          @blur="isLinkTouched = true"
          class="additem__input"
          :class="isValidName ? 'additem__input_error' : null"
          placeholder="Введите наименование товара"
        />
        <p class="additem__error" v-if="isValidName">{{ errorMessage }}</p>
      </div>
      <div class="additem__block">
        <label for="" class="additem__title">Описание товара</label>
        <input
          class="additem__input additem__input_description"
          v-model="item.desc"
          type="text"
          placeholder="Введите описание товара"
        />
      </div>
      <div class="additem__block">
        <div class="additem__label">
          <label for="" class="additem__title"
            >Ссылка на изображение товара</label
          >
          <span class="additem__required"></span>
        </div>
        <input
          v-model="item.link"
          type="url"
          placeholder="Введите ссылку"
          class="additem__input"
          :class="isValidLink ? 'additem__input_error' : null"
          @input="checkInput('link')"
        />
        <p class="additem__error" v-if="isValidLink">{{ errorMessage }}</p>
      </div>
      <div class="additem__block">
        <div class="additem__label">
          <label for="" class="additem__title">Цена товара</label>
          <span class="additem__required"></span>
        </div>
        <input
          v-model="item.price"
          class="additem__input"
          :class="isValidPrice ? 'additem__input_error' : null"
          @input="checkInput('price')"
          type="number"
          placeholder="Введите цену"
        />
      </div>
      <p class="additem__error" v-if="isValidPrice">{{ errorMessage }}</p>
      <button
        @click="addItem"
        type="submit"
        class="additem__button"
        :disabled="!isValid"
      >
        Добавить товар
      </button>
    </form>
  </div>
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
<style  scoped>
.additem {
  position: relative;
  padding: 24px;
  margin: 0 16px 0 0;
  max-width: 332px;
  width: 100%;
  height: 440px;
  background-color: rgba(255, 254, 251, 1);
  border-radius: 4px;
  box-sizing: border-box;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
}
.additem__form {
  width: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
.additem__error {
  position: absolute;
  bottom: -18px;
  margin: 0;
  font-size: 8px;
  color: rgba(255, 132, 132, 1);
}
.additem__block {
  position: relative;
  margin: 0 0 18px 0;
}
.additem__label {
  display: flex;
}
.additem__title {
  margin: 0 0 4px 0;
  font-size: 10px;
  font-weight: 400;
  line-height: 12px;
}
.additem__input {
  padding: 10px 16px;
  width: 100%;
  font-size: 12px;
  line-height: 15px;
  color: #3f3f3f;
  border: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  box-sizing: border-box;
}
.additem__input_error {
  outline: 1px solid rgba(255, 132, 132, 1);
}
.additem__input:last-child {
  margin: 0 0 0 0;
}
.additem__input_description {
  height: 108px;
  resize: none;
  font-family: "SourceSansPro", Helvetica, Arial;
  font-size: 12px;
  font-weight: 400;
  line-height: 15px;
  color: #3f3f3f;
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
</style>
