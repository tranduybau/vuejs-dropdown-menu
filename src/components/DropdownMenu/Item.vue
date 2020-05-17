<template>
  <div class="item" @click="doFunc">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Item',
  props: {
    item: {
      type: Object,
      required: true,
    },
    closeDropdown: {
      type: Function,
      default: () => {},
    },
  },
  methods: {
    doFunc() {
      console.log(this.item.link);
      this.closeDropdown();
    }
  }
};
</script>

<style lang="scss" scoped>
.item {
  display: block;
  width: 100%;
  padding: 5px 10px;
  transition: 0.3s;
  position: relative;

  &:hover {
    background: black;
    color: white;
  }
}
</style>
