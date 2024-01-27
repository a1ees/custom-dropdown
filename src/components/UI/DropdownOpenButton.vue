<template>
  <div class="burger">
  <burger-icon @click="this.$emit('clickBurger')" class="burger__icon"/>
    <slot></slot>
  </div>
</template>

<script>
import BurgerIcon from "@/components/icon/BurgerIcon.vue";

export default {
  components: {BurgerIcon}

}
</script>
<style lang="scss" scoped>
.burger {
  border: 1px solid #4AB4FF;
  background-color: #0E121B;
  display: flex;
  max-width: 24px;
  &__icon {
    padding: 4px;
  }
  &:hover {
    cursor: pointer;
  }
}
</style>
