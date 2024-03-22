<template>
  <div id="app">
    <ShoppingList />
  </div>
</template>

<script>
import ShoppingList from './components/ShoppingList.vue';

export default {
  components: {
    ShoppingList
  }
};
</script>

<style>
.shopping-list {
  max-width: 600px;
  margin: 0 auto;
}

.item-list,
.cart-list {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 20px;
}

.item-list th,
.cart-list th {
  text-align: left;
  padding: 8px;
  background-color: #f2f2f2;
}

.item-list td,
.cart-list td {
  padding: 8px;
}

.input {
  display: flex;
  justify-content: center;
}

.item-input {
  width: 330px;
  padding: 8px;
  margin-right: 10px;
  align-items: 10px;
}

.qty-input,
.edit-qty {
  width: 100px;
  padding: 8px;
  margin-right: 10px;
}

.add-button,
.remove-button,
.edit-button {
  padding: 8px 16px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-button:hover,
.remove-button:hover {
  background-color: #45a049;
}

.total {
  font-weight: bold;
  font-size: 18px;
}
</style>
