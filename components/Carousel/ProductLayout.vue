<template>
  <div v-if="prod" class="product" :style="`background-color: ${bgType(prod)}`">
    <ProductCard :prod="prod" />
    <button
      class="product__button product__button--comprar"
      @click="SET_ITEM_CART(prod)"
    >
      {{ $t('carousel[1]') }}
    </button>
    <a href="#contact" class="product__button product__button--falar">{{
      $t('carousel[2]')
    }}</a>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { mapActions } from 'vuex'
import colorCard from '@/mixins/colorCard'
import { EnumActionsCart } from '~/store/cart/cart.type'
export default Vue.extend({
  name: 'ProductslayoutComponent',
  mixins: [colorCard],
  props: {
    prod: {
      type: Object,
      required: true,
    },
  },
  methods: {
    ...mapActions({
      SET_ITEM_CART: `cart/${EnumActionsCart.SET_ITEM_CART}`,
    }),
  },
})
</script>

<style lang="scss" scoped>
.product {
  width: 250px;

  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 15px;
  padding: 40px 0 50px 0;
  &__button {
    width: 80%;
    height: 50px;
    border: none;
    border-radius: 10px;
    margin-top: 20px;
    font-size: 16px;
    font-weight: bold;
    color: white;
    cursor: pointer;
    transition: all 0.1s ease-in-out;
    &:hover {
      transition: all 0.1s ease-in-out;
      transform: scale(1.02);
    }
  }
  &__button--comprar {
    background-color: #f78600;
    box-shadow: 3px 3px #c26c03;
  }
  &__button--falar {
    background-color: #1686f0;
    box-shadow: 3px 3px #004d95;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
  }
}
@media (min-width: 1024px) {
  .product {
    width: 300px;
    padding: 60px 0 50px 0;
  }
}
</style>
