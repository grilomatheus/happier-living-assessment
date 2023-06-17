<template>
  <div class="card">
    <div class="card-header">
      <div class="avatar">{{ items.length }}</div>
      <h2>{{ cardName }}</h2>
    </div>
    <hr>
    <div class="content" v-if="items.length > 0">
      <ul>
        <li v-for="(item, index) in items" :key="index" @click="removeItem(index)">
          {{ item }}
        </li>
      </ul>
    </div>
    <div class="content" v-else>
      <p>No items added yet. Start adding some!</p>
    </div>
    <hr>
    <button role="button" @click="addItem">Add Item</button>
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
  
<style scoped>
.card {
  display: flex;
  flex-direction: column;
  border: 1px solid #b6b6b6;
  border-top: 4px solid #936fdb;
  border-radius: 4px;
  padding: 20px;
  margin-bottom: 20px;
  background-color: #f3f3f3;
  flex-grow: 1;
}
.card-header {
  display: flex;
  align-items: center;
  gap: 10px;
}

.avatar {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #636363;
  color: white;
  font-size: 16px;
}
  
.content ul {
  list-style-type: none;
  padding: 0;
}

.content ul li {
  cursor: pointer;
  padding: 10px 0;
  border-bottom: 1px solid #ddd;
}

.content ul li:last-child {
  border-bottom: none;
}

button {
  margin-top: auto;
  padding: 10px;
  border: none;
  background-color: #1c50a9;
  color: white;
  cursor: pointer;
  border-radius: 50px;
}

button:focus {
  outline: 2px solid #936fdb;
}

button:hover {
  background-color: #0056b3;
}
  </style>
  