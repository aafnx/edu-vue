<template>
  <div id="app">
    <div class="buttons">
      <button @click="changeCurrency('usd')">show in usd</button>
      <button @click="changeCurrency('rub')">show in rub</button>
    </div>
    <ProductDetails
        v-for="product in products" :key="product.id"
        :productData="product" :currency="selectedCurrency" />
  </div>
</template>

<script>
/* eslint-disable import/no-extraneous-dependencies */
import ProductDetails from '@/components/ProductDetails.vue';

export default {
  name: 'App',
  components: {
    ProductDetails,
  },
  data() {
    return {
      selectedCurrency: 'usd',
      products: [
        {
          id: 1,
          name: 'Mock 1',
          price: { usd: 99.99, rub: 999.99 },
          available: false,
        },
        {
          id: 2,
          name: 'Mock 2',
          price: { usd: 159.99, rub: 1599.99 },
          available: true,
        },
        {
          id: 3,
          name: 'Mock 3',
          price: { usd: 219.99, rub: 2199.99 },
          available: true,
        },
      ],
    };
  },
  methods: {
    changeCurrency(currency = 'usd') {
      this.selectedCurrency = currency;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: grid;
  grid-template-columns: repeat(3, 360px);
  gap: 20px;
  justify-content: center;
}

.buttons {
  grid-column: 1 / -1;
}
</style>
