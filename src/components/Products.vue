<template>
  <div>
  <ul class="products-listing">
    <li v-for="product in allproducts" :key="product.id">
      {{product.title}} - {{product.price | currency }}
      <button @click="deleteProduct(product.id)">❌</button>
    </li>
  </ul>
  </div>
</template>
<script>
import { mapGetters, mapActions } from 'vuex';
export default {
  name:"StoreProducts",
  filters:{
    currency: function(value){
      return "₹ " + parseFloat(value).toFixed(2);
    }
  },
  methods:{
    ...mapActions(['getProducts','deleteProduct'])
  },
  created(){
    this.getProducts();
  },
  computed: mapGetters(["allproducts"])
}
</script>
<style scoped>
  .products-listing li {
  background: #fff;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 20px;
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.products-listing li button {
  background: #fff;
  border: 1px solid #fff;
  border-radius: 5px;
  color: #000;
  font-size: 16px;
  cursor: pointer;
}
</style>
