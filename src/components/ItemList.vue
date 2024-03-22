<template>
    <div class="input">
      <input type="text" v-model="newItem" class="item-input" placeholder="Enter Item">
      <input class="qty-input" type="number" v-model="newItemQuantity" placeholder="QTY">
      <button class="add-button" @click="addItem">Add</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newItem: '',
        newItemQuantity: 1
      };
    },
    props: {
      items: {
        type: Array,
        required: true
      }
    },
    methods: {
      addItem() {
        if (this.newItem.trim() === '') {
          alert('Enter Item First');
          return;
        }
  
        const foundItem = this.items.find(item => item.name.toLowerCase() === this.newItem.toLowerCase());
        if (!foundItem) {
          alert('Item not found');
          return;
        }
  
        this.$emit('add-item', {
          name: foundItem.name,
          cost: foundItem.cost,
          quantity: this.newItemQuantity,
          editing: false,
          newQuantity: 1
        });
  
        this.newItem = '';
        this.newItemQuantity = 1;
      }
    }
  };
  </script>
  
  
