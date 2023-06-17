<template>
  <div id="app">
    <CustomNavbar/>
    <div class="container">
      <div class="content-container">
        <h1>Item Counter: {{ totalItems }}</h1>
        <div class="cards">
          <CustomCard cardName="Card 1" @itemAdded="incrementItem" @itemRemoved="decrementItem"/>
          <CustomCard cardName="Card 2" @itemAdded="incrementItem" @itemRemoved="decrementItem"/>
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

<style>
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  width: 100%;
  padding: 20px;
  box-sizing: border-box;
  margin: auto;
}

.content-container {
  max-width: 1200px;
  width: 100%;
  margin: auto;
}

h1 {
  text-align: left;
  margin-bottom: 20px;
}
.cards {
  display: flex;
  justify-content: space-between;
  gap: 20px;
  flex-direction: row;
}

.cards > * {
  flex-basis: calc(50% - 20px);
}

@media (max-width: 768px) {
  .cards {
    flex-direction: column;
  }

  .cards > * {
    flex-basis: 100%;
  }
}
</style>
