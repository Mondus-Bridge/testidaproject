<template>
  <div class="container">
    <div>
      <img class="img__link" :src="item.link" />
      <div class="container__text">
        <div>{{ item.title }}</div>
        <div>{{ item.desc }}</div>
        <div>{{ money(item.price) }}</div>
      </div>
    </div>
    <div>
      <a @click="$emit('remove', item)"
        ><img class="remove__icon" src="../assets/icons/trash-alt-solid.svg"
      /></a>
    </div>
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
  flex-direction: column;
  background: #fffefb;
}

.container__text {
  display: flex;
  flex-direction: column;
}

a {
  position: relative;
  right: 37px;
  top: -5px;
  width: 10px;
  height: 10px;
}

.remove__icon {
  background: #ff8484;
  padding: 10px;
  width: 32px;
  height: 32px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
}

.img__link {
  width: 332px;
  height: 200px;
  object-fit: cover;
  border-radius: 4px 4px 0px 0px;
}
</style>
