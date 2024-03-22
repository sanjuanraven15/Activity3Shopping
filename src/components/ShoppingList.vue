<template>
    <div class="shopping-list">
        <h1>Shopping List</h1>
        <hr>
        <table class="item-list">
            <thead>
                <tr>
                    <th>Item</th>
                    <th>Price</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Pencil</td>
                    <td>₱8</td>
                </tr>
                <tr>
                    <td>Ballpen</td>
                    <td>₱10</td>
                </tr>
                <tr>
                    <td>Marker</td>
                    <td>₱15</td>
                </tr>
                <tr>
                    <td>Bond Paper</td>
                    <td>₱1</td>
                </tr>
                <tr>
                    <td>Sticky Notes</td>
                    <td>₱10</td>
                </tr>
                <tr>
                    <td>Yellow Pad</td>
                    <td>₱25</td>
                </tr>
                <tr>
                    <td>Notebook</td>
                    <td>₱32</td>
                </tr>
                <tr>
                    <td>Eraser</td>
                    <td>₱5</td>
                </tr>
                <tr>
                    <td>Colored Paper</td>
                    <td>₱2</td>
                </tr>
                <tr>
                    <td>Scissor</td>
                    <td>₱28</td>
                </tr>
            </tbody>
        </table>
        <ItemList :items="items" @add-item="addItem" />
        <ShoppingCart :cart="cart" @remove-item="removeItem" @toggle-editing="toggleEditing"
            @update-quantity="updateQuantity" />
        <p class="total">Total of items: ₱{{ calculateTotal() }}</p>
    </div>
</template>

<script>
import ItemList from './ItemList.vue';
import ShoppingCart from './ShoppingCart.vue';

export default {
    components: {
        ItemList,
        ShoppingCart,
    },
    data() {
        return {
            items: [
                { name: 'Pencil', cost: 8 },
                { name: 'Ballpen', cost: 10 },
                { name: 'Marker', cost: 15 },
                { name: 'Bond Paper', cost: 1 },
                { name: 'Sticky Notes', cost: 10 },
                { name: 'Yellow Pad', cost: 25 },
                { name: 'Notebook', cost: 32 },
                { name: 'Eraser', cost: 5 },
                { name: 'Colored Paper', cost: 2 },
                { name: 'Scissor', cost: 28 }
            ],
            cart: []
        };
    },
    methods: {
        addItem(item) {
            this.cart.push(item);
        },
        removeItem(index) {
            this.cart.splice(index, 1);
        },
        calculateTotal() {
            return this.totalPrice;
        },
        toggleEditing(index) {
            this.cart[index].editing = true;
            this.cart[index].newQuantity = this.cart[index].quantity;
        },
        updateQuantity(payload) {
            const { index, newQuantity } = payload;
            if (newQuantity <= 0) {
                alert('Quantity must be greater than zero');
                return;
            }
            this.cart[index].quantity = newQuantity;
            this.cart[index].editing = false;
        }
    },
    computed: {
        totalPrice() {
            return this.cart.reduce((total, item) => total + (item.cost * item.quantity), 0);
        }
    },
};
</script>