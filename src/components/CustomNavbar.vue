<template>
  <nav class="custom-navbar">
    <div class="custom-navbar__container">
      <div class="custom-navbar__name">{{ name }}</div>
      <div class="custom-navbar__date">{{ currentDate }}</div>
    </div>
  </nav>
</template>
  
<script>
export default {
  name: 'CustomNavbar',
  data() {
    return {
      name: 'Matheus',
      currentDate: new Date().toLocaleString()
    }
  }
}
</script>
  
<style lang="scss" scoped>
@import '../assets/_variables.scss';
.custom-navbar {
  display: flex;
  justify-content: center;
  padding: 20px;
  background-color: #f8f9fa;

  &__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    width: 100%;
  }

  &__name {
    font-size: 24px;
  }

  &__date {
    font-size: 16px;
  }
}
</style>
  