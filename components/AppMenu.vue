<template>
  <nav>
    <ul>
      <li>
        <nuxt-link to="/"><AppLogo /></nuxt-link>
      </li>
      <li><nuxt-link to="/restaurants">Restaurants</nuxt-link></li>
    </ul>
    <div class="smallnum">{{ cartTotal }}</div>
    <nuxt-link to="/cart">Cart</nuxt-link>
  </nav>
</template>

<script>
import AppLogo from "@/components/AppLogo.vue";
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapGetters(["cartTotal"]),
  },
  components: {
    AppLogo,
  },
};
</script>

<style lang="scss" scoped>
</style>