<template>
    <li class="dropdown__item">
      <slot></slot>
    </li>
</template>

<script>
export default {
  data() {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
.dropdown__item {
  all: unset;
  background-color: #212B41;
  padding: 6px 12px;
  width: 100%;
  box-sizing: border-box;

  display: flex;
  align-items: center;
  gap: 6px;

  font-family: "Gotham Pro", sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 20px;
  letter-spacing: 0.252px;
  transition: background-color 0.3s ease;

  &:hover {
    background-color: #303F5F;
    cursor: pointer;
  }

}
</style>
