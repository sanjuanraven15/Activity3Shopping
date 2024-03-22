<template>
    <div class="cart">
      <h2>Cart:</h2>
      <table class="cart-list">
        <thead>
          <tr>
            <th>Item</th>
            <th>Price</th>
            <th>Quantity</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in cart" :key="index">
            <td>{{ item.name }}</td>
            <td>₱{{ item.cost }}</td>
            <td v-if="!item.editing">{{ item.quantity }}</td>
            <td v-else>
              <input class="edit-qty" type="number" v-model="item.newQuantity">
            </td>
            <td>
              <button v-if="!item.editing" class="remove-button" @click="removeItem(index)">Remove</button>
              | <button v-if="!item.editing" class="edit-button" @click="toggleEditing(index)">Edit Quantity</button>
              <button v-else class="edit-button" @click="updateQuantity(index)">Save</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cart: {
        type: Array,
        required: true
      }
    },
    methods: {
      removeItem(index) {
        this.$emit('remove-item', index);
      },
      toggleEditing(index) {
        this.$emit('toggle-editing', index);
      },
      updateQuantity(index) {
        this.$emit('update-quantity', { index, newQuantity: this.cart[index].newQuantity });
      }
    }
  };
  </script>
  
  