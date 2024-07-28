<template>
  <header>
    <v-toolbar>
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/50/Dm_Logo.svg/1200px-Dm_Logo.svg.png" alt="Company logo." width="40">
      <v-toolbar-title>Corner Shop</v-toolbar-title>
      <v-btn
          @click="router.push({ name: 'CartView' })"
          color="primary"
          variant="plain"

      >Items in Cart: {{ store.cart.length }}
      </v-btn>
    </v-toolbar>
  </header>
  <main>
    <RouterView />
  </main>
  
</template>

<script setup>
  import { useRouter } from "vue-router";
  import { productsStore } from "@/stores/products";

  const router = useRouter()
  const store = productsStore()
</script>


<style scoped>
.cart-items {
  text-align: end;
  padding: 16px;
  font-weight: bold;
  font-size: 24px;
  cursor: pointer;
}
</style>
