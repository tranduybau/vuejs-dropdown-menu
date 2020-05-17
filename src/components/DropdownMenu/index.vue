<template>
  <div :id="id" class="dropdown">
    <button @click="isOpen = !isOpen" :class="{ isActive: isOpen }">
      <slot />
    </button>
    <div class="dropdown-list" v-if="isOpen">
      <Item
        v-for="(item, index) in arrays"
        :key="index"
        :item="item"
        :closeDropdown="callToClose"
      >
        {{ item.text }}
      </Item>
    </div>
  </div>
</template>

<script>
import Item from './Item';

export default {
  name: 'DropdownMenu',
  components: {
    Item,
  },
  data() {
    return {
      isOpen: false,
    };
  },
  created() {
    window.addEventListener('click', this.checkClickOn);
  },
  beforeDestroy() {
    window.removeEventListener('click', this.checkClickOn);
  },
  props: {
    arrays: {
      type: Array,
      default: () => [],
    },
    id: {
      type: String,
      required: true,
    },
  },
  methods: {
    callToClose() {
      this.isOpen = false;
    },
    checkClickOn(event) {
      if (!document.getElementById(this.id).contains(event.target)) {
        this.isOpen = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  position: relative;
  padding: 10px 20px;
  background-color: white;
  border: 1px solid black;
  cursor: pointer;
  transition: 0.3s;

  &:focus {
    outline: 0px;
  }

  &:hover {
    background: #000;
    color: white;
  }

  &.isActive {
    background: #000;
    color: white;
  }
}

.dropdown {
  position: relative;
  width: fit-content;

  &-list {
    background: white;
    margin-top: 5px;
    position: absolute;
    z-index: 10;
    width: 100%;
    border: 1px solid black;
    border-radius: 4px;
  }
}
</style>
