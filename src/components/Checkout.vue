<template>
  <div>
    <h1>Checkout</h1>

    <table v-if="cart.length" class="table table-hover">
      <caption class="text-right h3">
        <b>Total:</b>
        <price
          class="d-block text-success font-weight-light"
          :value="Number(cartTotal)"
        />
      </caption>
      <thead>
        <tr>
          <th scope="col" />
          <th scope="col">Item</th>
          <th scope="col" class="text-center">Qty</th>
          <th scope="col" class="text-right">Price</th>
          <th scope="col" class="text-right">Sub-total</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in cart" :key="item.product.id">
          <td class="text-center">
            <div class="btn-group" role="group" aria-label="Basic example">
              <button class="btn btn-info" @click="$emit('add', item.product)">
                +
              </button>
              <button
                @click="$emit('delete', index)"
                class="btn btn-outline-info"
              >
                -
              </button>
            </div>
          </td>
          <th scope="row">{{ item.product.name }}</th>
          <td class="text-center">{{ item.qty }}</td>
          <td class="text-right">{{ Number(item.product.price) }}</td>
          <td class="text-right">
            {{ Number(item.qty * item.product.price) }}
          </td>
        </tr>
      </tbody>
    </table>
    <router-link class="btn btn-sm btn-outline-info text-dark" to="/"
      >Keep Shopping</router-link
    >
  </div>
</template>

<script>
import VueRouter from 'vue-router'
import Price from './Price.vue'

export default {
  name: 'Checkout',
  components: {
    Price
  },
  props: ['cart', 'cartTotal']
}
</script>
