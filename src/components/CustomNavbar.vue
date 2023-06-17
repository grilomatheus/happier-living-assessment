<template>
  <nav>
    <div class="navbar">
      <div class="navbar-container">
        <div class="name">{{ name }}</div>
        <div class="date">{{ currentDate }}</div>
      </div>
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
  
<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  justify-content: center;
  padding: 20px;
  background-color: #f8f9fa;
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  width: 100%;
}

.name {
  font-size: 24px;
}

.date {
  font-size: 16px;
}
</style>
  