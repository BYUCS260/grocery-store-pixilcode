<template>
  <div class="wrapper">
    <div class="cartTitle">
      <h1>Your Cart</h1>
    </div>
    <div id="emptyMessage" v-if="cart.length === 0">
      <p>Your cart is empty!</p>
    </div>
    <div id="cart">
      <div class="item" v-for="item in cart" :key="item.id">
        <div class="info">
          <h3>{{ item.name }}</h3>
          <p>{{ item.country }}</p>
        </div>
        <div class="image">
          <img :src="'/images/products/' + item.image" />
        </div>
        <div class="price">
          <h2>{{ item.price }}</h2>
          <button class="auto" @click="removeFromCart(item)">Remove</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CartView",
  computed: {
    cart() {
      return this.$root.$data.cart;
    },
  },
  methods: {
    removeFromCart(item) {
      this.$root.$data.cart.splice(this.$root.$data.cart.indexOf(item), 1);
    },
  },
};
</script>

<style scoped>
#emptyMessage {
  text-align: center;
  font-size: 50px;
  color: #ad2e00;
}

#cartTitle {
  text-align: center;
}

#cart {
  display: grid;
  grid-template-columns: auto auto auto 1fr;
  width: auto;
}

.item {
  grid-column: span 3;
  display: grid;

  grid-template-columns: subgrid;
  grid-auto-flow: row;

  margin: 10px 0;
  height: 125px;

  justify-content: right;
}

.info {
  background-color: #f2921d;
  padding: 10px;
  margin: 0;
}

.image img {
  border: 2px solid #333;
  height: 100%;
  width: 100px;
  object-fit: cover;
}

.price {
  background-color: #aaa;
  padding: 10px;
}
</style>
