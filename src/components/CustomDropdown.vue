<template>
  <dropdown-open-button ref="dropdownButton" class="dropdown" @clickBurger="toggleDropdown">
    <ul v-if="isOpen" :class="`dropdown__list ${calcButtonPlace}`">
    <drop-down-li
          v-for="(item, index) in dropdownItems"
          :key="index"
          :class="{'selected': selectedElement === item.text}"
          class="dropdown__list-items"
          @click="setSelectedElement(item)"
      >
        <component
            :is="item.icon"
            v-if="item.icon"
        />
        {{ item.text }}
      </drop-down-li>
    </ul>
  </dropdown-open-button>
</template>

<script>
import DropDownLi from "./UI/DropdownLi.vue";
import PicturesIcon from "@/components/icon/PicturesIcon.vue";
import DropdownOpenButton from "@/components/UI/DropdownOpenButton.vue";

export default {
  components: {DropdownOpenButton, DropDownLi, PicturesIcon},
  props: {
    dropdownItems: {
      type: Array,
    },
  },
  data() {
    return {
      selectedElement: '',
      isOpen: false,
    };
  },
  mounted() {
    window.addEventListener('click', this.handleWindowClick);
  },
  computed: {
    calcButtonPlace() { //возвращает класс, отвечающий за расположение элемента
      const coordinatesButton = this.$refs.dropdownButton.$el.getBoundingClientRect() // получаем координаты нашей кнопки
      const windowWidth = window.innerWidth;
      const windowHeight = window.innerHeight;
      const {x, y} = coordinatesButton;

      if (windowWidth / 2 > x) {
        if (windowHeight / 2 > y) { // кнопка находится в левой верхней стороне окна
          return 'bottomRight'
        } else { // кнопка находится в левой нижней стороне окна
          return 'topRight'
        }
      } else {
        if (windowHeight / 2 > y) { // кнопка находится в правой верхней стороне окна
          return 'bottomLeft'
        } else { // кнопка находится в правой нижней стороне окна
          return 'topLeft'
        }
      }
    },
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen
    },
    setSelectedElement(item) {
      if (this.selectedElement !== item.text) {
        this.selectedElement = item.text;
      } else {
        this.selectedElement = '';
      }
    },
    handleWindowClick(event) {
      if (this.$refs.dropdownButton && this.isOpen) {
        if (!this.$refs.dropdownButton.$el.contains(event.target)) {
          this.isOpen = false;
        }
      }
    }
  },
  watch: {
    isOpen() {
      this.selectedElement = '';
    }
  }
};
</script>

<style lang="scss" scoped>
.dropdown {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  position: relative;

  &__list {
    list-style: none;
    padding: 0;
    margin: 0;

    position: absolute;
    width: 200px;

    display: flex;
    flex-direction: column;
    gap: 1px;
    border-radius: 2px;
    overflow: hidden;
    box-shadow: 0 0 6px 0 rgba(0, 0, 0, 0.75);
  }
}
.bottomRight {
  top: 107%;
  left: calc(100% - 24px);
}
.topRight {
  bottom: 107%;
  left: calc(100% - 24px);
}
.bottomLeft {
  top: 107%;
  right: calc(100% - 24px);
}
.topLeft {
  bottom: 107%;
  right: calc(100% - 24px);
}

.selected {
  border-left: 2px solid #4AB4FF;
  background: #151B29;
  transition: background 0.3s ease;

  &:hover {
    background: #151B29;
  }
}
</style>

