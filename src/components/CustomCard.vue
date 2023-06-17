<template>
  <div class="custom-card">
    <div class="custom-card__header">
      <div class="custom-card__avatar">{{ items.length }}</div>
      <h2 class="custom-card__name">{{ cardName }}</h2>
    </div>
    <hr class="custom-card__divider">
    <div class="custom-card__content" v-if="items.length > 0">
      <ul class="custom-card__list">
        <li class="custom-card__item" v-for="(item, index) in items" :key="index" @click="removeItem(index)">
          {{ item }}
        </li>
      </ul>
    </div>
    <div class="custom-card__content custom-card__content--empty" v-else>
      <p>No items added yet. Start adding some!</p>
    </div>
    <hr class="custom-card__divider">
    <button class="custom-card__button" role="button" @click="addItem">Add Item</button>
  </div>
</template>
  
<script>
export default {
  name: 'CustomCard',
  props: {
    cardName: {
      type: String,
      default: 'Card'
    }
  },
  data() {
    return {
      items: []
    }
  },
  methods: {
    addItem() {
      this.items.push(`Item #${this.items.length + 1}`);
      this.$emit('itemAdded');
    },
    removeItem(index) {
      this.items.splice(index, 1);
      this.$emit('itemRemoved');
    }
  }
}
</script>
  
<style lang="scss" scoped>
@import '../assets/_variables.scss';
.custom-card {
  display: flex;
  flex-direction: column;
  border: 1px solid $color-grey;
  border-top: 4px solid $color-secondary;
  border-radius: 4px;
  padding: 20px;
  margin-bottom: 20px;
  background-color: $color-light-grey;
  flex-grow: 1;
  
  &__header {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  
  &__avatar {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: $color-dark-grey;
    color: $color-white;
    font-size: 16px;
  }
  
  &__content {
    & ul {
      list-style-type: none;
      padding: 0;
  
      & li {
        cursor: pointer;
        padding: 10px 0;
        border-bottom: 1px solid $color-light-grey;
  
        &:last-child {
          border-bottom: none;
        }
      }
    }
  }
  
  &__button {
    margin-top: auto;
    padding: 10px;
    border: none;
    background-color: $color-primary;
    color: $color-white;
    cursor: pointer;
    border-radius: 50px;
  
    &:focus {
      outline: 2px solid $color-secondary;
    }
  
    &:hover {
      background-color: darken($color-primary, 10%);
    }
  }
}
  </style>
  