<template>
  <div class="products-list">
    
    <v-row no-gutters>
      <v-col
          v-for="product in store.products"
          :key="product.id"
          cols="12"
          sm="4"
          @click="goToProductPage(product.id)"
      >
        <product-item
            :product-data="product"
            @item-clicked="goToProductPage"
        />
      </v-col>
    </v-row>

    </div>
    <footer>
    <v-toolbar>
      <v-toolbar-title>© DM Corner Shop</v-toolbar-title>
      <v-btn color="primary" variant="plain"><a href="https://www.dm-drogeriemarkt.ba/rasprodaja">See full list of products</a></v-btn>
    </v-toolbar>
    <p style="font-size: 10px;">Have in mind that this is just a portfolio project by Teanej Urošević, and it doesn't showcase any true info about the DM company.</p>
  </footer>
</template>

<script>
  import { defineComponent } from "vue";
  import ProductItem from "@/components/ProductItem.vue";
  export default defineComponent({
    name: 'CatalogView',
    components: {
      ProductItem
    }
  })
</script>

<script setup>
  import { onMounted, ref } from "vue";
  import { productsStore } from "@/stores/products";
  import { useRouter } from "vue-router";

  const store = productsStore()
  const router = useRouter()


  const goToProductPage = (id) => {
    router.push({ name: 'ProductView', params: { id } })
  }


  onMounted(async () => {
    await store.fetchProductsFromDB()
  })
</script>

<style scoped>

</style>