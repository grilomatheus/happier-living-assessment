<template>
  <div class="app">
    <CustomNavbar class="app__navbar"/>
    <div class="app__container">
      <div class="app__content">
        <h1 class="app__title">Item Counter: {{ totalItems }}</h1>
        <div class="app__cards">
          <CustomCard class="app__card" cardName="Card 1" @itemAdded="incrementItem" @itemRemoved="decrementItem"/>
          <CustomCard class="app__card" cardName="Card 2" @itemAdded="incrementItem" @itemRemoved="decrementItem"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CustomNavbar from './components/CustomNavbar.vue'
import CustomCard from './components/CustomCard.vue'

export default {
  name: 'App',
  components: {
    CustomNavbar,
    CustomCard
  },
  data() {
    return {
      totalItems: 0
    }
  },
  methods: {
    incrementItem() {
      this.totalItems += 1;
    },
    decrementItem() {
      this.totalItems -= 1;
    }
  }
}
</script>

<style lang="scss">
@import './assets/_variables.scss';
body {
  margin: 0;
}

.app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $color-black;
  margin-top: 60px;

  &__container {
    width: 100%;
    padding: 20px;
    box-sizing: border-box;
    margin: auto;
  }
  
  &__content {
    max-width: 1200px;
    width: 100%;
    margin: auto;
  }
  
  &__title {
    text-align: left;
    margin-bottom: 20px;
  }
  
  &__cards {
    display: flex;
    justify-content: space-between;
    gap: 20px;
    flex-direction: row;

    & > .app__card {
      flex-basis: calc(50% - 20px);
    }
  }
  
  @media (max-width: 768px) {
    &__cards {
      flex-direction: column;

      & > .app__card {
        flex-basis: 100%;
      }
    }
  }
}
</style>
