<template>
  <main class="container cart">
    <h2>Your Cart</h2>
    <div v-if="!cart.length" class="empty">
      <AppCartEmty />
      <h2>Your cart is empty!</h2>
      <button><nuxt-link to="/restaurants">Fill it up!</nuxt-link></button>
    </div>
    <div v-else>
      <table>
        <thead>
          <tr>
            <th>Item</th>
            <th>Add Ons</th>
            <th>Amount</th>
            <th>Total Price</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in cart" :key="item.id">
            <td>
              {{ item.item }}
              <span v-if="item.options">{{ item.option }}</span>
            </td>
            <td>
              <span v-for="addon in item.addOns" :key="addon" class="comma">{{
                addon
              }}</span>
            </td>
            <td>{{ item.count }}</td>
            <td>{{ item.combinedPrice }}</td>
          </tr>
          <tr>
            <td colspan="3"></td>
            <td class="total">Total: ${{ totalPrice.toFixed(2) }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </main>
</template>

<script>
import { mapState, mapGetters } from "vuex";
import AppCartEmty from "@/components/AppCartEmty.vue";
export default {
  components: {
    AppCartEmty,
  },
  computed: {
    ...mapState(["cart"]),
    ...mapGetters(["totalPrice"]),
  },
};
</script>

<style lang="scss" scoped>
.empty {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>