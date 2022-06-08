<template>
  <div class="main-navigation__list">
    <ul>
      <MenuItem
        v-for="(item, index) in menu"
        :key="index"
        :model="item"
        :link-start="`/catalog`"
        :link-end="item.slug"
      />
    </ul>
  </div>
</template>

<script>
import MenuItem from './MenuItem';

export default {
  name: 'HeaderMenu',
  components: { MenuItem },
  data() {
    return {
      menu: [],
    };
  },
  mounted() {
    this.menu = this.$store.state.the_menu.menu;
  },
};
</script>

<style scoped lang="scss">
@import "~assets/variables.scss";

.main-navigation {
  &__list {
    position: absolute;
    top: 100%;right: -100%;
    height: calc(100vh - 104px);
    overflow-y: auto;
    width: 100vw;
    transition: all .3s linear;
    padding: 1rem;
    background: #6004ba;
    z-index: 9999;
    @media (min-width: $screen-md) {
      width: 400px;
      height: 500px;
      right: unset;
      left: 132px;
      opacity: 0;
      visibility: hidden;
      &::-webkit-scrollbar {
        background-color: transparent;
        width: 6px;
      }
      &::-webkit-scrollbar-thumb {
        background-color: $white;
        border-radius: 5px;
      }
      &::-webkit-scrollbar-track {
        padding: 2px 4px;
      }
    }
    &--opened {
      right: 0;
      @media (min-width: $screen-md) {
        right: unset;
        opacity: 1;
        visibility: visible;
      }
    }
  }
}
</style>
