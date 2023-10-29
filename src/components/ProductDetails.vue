<script>
export default {
  name: 'ProductDetails',
  props: {
    productData: {
      type: Object,
      required: true,
    },
    currency: {
      type: String,
      required: false,
      default: 'usd',
    },
  },
  computed: {
    formattedPrice() {
      switch (this.currency) {
        case 'rub': {
          return `${this.productData.price.rub} ₽`;
        }
        default: {
          return `$ ${this.productData.price.usd}`;
        }
      }
    },
  },
};
</script>

<template>
  <article class="product">
    <h3 class="product-name">{{ productData.name }}</h3>
    <p class="price">{{ formattedPrice }}</p>
    <p v-if="productData.available" class="available">Avialable</p>
    <p v-else class="not-available">Out of stock</p>
  </article>
</template>

<style scoped>
.product {
  border: 1px solid #000;
  padding: 20px 10px;
  max-width: 360px;
  background-color: #ccc;
}
.product-name {
  color: mediumpurple;
}

.available {
  background-color: green;
}

.not-available {
  background-color: rosybrown;
}

</style>
