<template>
  <div class="container__item">
    <div class="item__item">
      <div>
        <button class="remove__icon" @click="$emit('remove', item)"></button>
        <img class="img__link" :src="item.link" />
      </div>
      <div class="container__text">
        <div class="item__title">{{ item.title }}</div>
        <div class="item__desc">{{ item.desc }}</div>
        <div class="item__price">{{ money(item.price) }}</div>
      </div>
    </div>
    <div></div>
  </div>
</template>
<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  methods: {
    money(value) {
      const formatValue = new Intl.NumberFormat("ru-RU").format(value);
      if (!value) return "";
      return `${formatValue} руб.`;
    },
  },
};
</script>

<style lang="scss" scoped>
div {
  display: flex;
  position: relative;
  flex-direction: column;
  background: #fffefb;
}

.container__text {
  display: flex;
  flex-direction: column;
}

a {
  position: relative;
  right: -310px;
  top: -5px;
  width: 10px;
  height: 10px;
}

.item__title {
  margin: 16px 0;
  font-family: "SourceSansPro", Helvetica, Arial;
  font-weight: 600;
  font-size: 20px;
  line-height: 25px;
}

.item__desc {
  margin: 0;
}
.item__price {
  margin: auto 0 0 0;
  font-size: 24px;
  font-weight: 600;
  line-height: 30px;
}

.img__link {
  width: 332px;
  height: 200px;
  object-fit: cover;
  border-radius: 4px 4px 0px 0px;
  cursor: pointer;
}

.remove__icon {
  padding: 0;
  display: none;
  position: absolute;
  top: -8px;
  right: -8px;
  width: 32px;
  height: 32px;
  border: none;
  background-image: url("../assets/icons/trash-alt-solid.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-color: rgba(255, 132, 132, 1);
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  cursor: pointer;
  transition: 0.4s;
  z-index: 999;
}

.item__item:hover .remove__icon {
  display: block;
}
</style>
