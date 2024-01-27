<template>
  <div class="page">
    <div class="content">
      <custom-dropdown :dropdownItems="dropdownItems" class="custom-dropdown"/>
    </div>
  </div>
</template>

<script>
import "./assets/vendor/normalize.css"
import "./assets/vendor/fonts/fonts.css"
import CustomDropdown from "@/components/CustomDropdown.vue";

export default {
  name: 'App',
  components: {CustomDropdown},
  data() {
    return {
      dropdownItems: [
        {text: "Первый"},
        {text: "Второй"},
        {text: "Третий"},
        {text: "Четвертый"},
        {text: "Пятый", icon: "pictures-icon"},
        {text: "Шестой", icon: "pictures-icon"},
      ],
    }
  }
}
</script>

<style lang="scss" scoped>
.page {
  background-color: #0E121B;
  color: #fff;
  height: 100vh;
  padding: 0 10px;
}
.content {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
}

</style>
