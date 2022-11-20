<template>
  <ProductList @delete:product="deleteProduct" :products ="products"/>
  <AddProduct @add:product="addProduct"/>
</template>

<script>
import ProductList from './components/ProductList.vue'
import AddProduct from './components/AddProduct.vue'
export default {
  name: 'App',
  components: {
    ProductList,
    AddProduct
  },
  data(){
    return {
      products:[
        {
          id:1,
          productName: 'Laptop',
          price: 5000,
          quantity: 4
        },
        {
          id:2,
          productName: 'Keyboard',
          price: 300,
          quantity: 12
        },
        {
          id:3,
          productName: 'Mouse',
          price: 200,
          quantity: 5
        }
      ]
    }
  },
  methods:{
    deleteProduct(product){
      this.products = this.products.filter(
        p=> p.id != product.id
      )
    },
    addProduct(product){
      const newProduct = {...product}
      this.products = [...this.products, newProduct]
      console.log(this.products)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
