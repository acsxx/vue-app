<template>
  <div class="container border" id="addProduct">
    <form @submit.prevent ="handleAdd">
      <div class="form-group">
        <label for="id">Id</label>
        <input v-model="product.id" type="text" class="form-control" id="id"/>
      </div>
      <div class="form-group">
        <label for="product-name">Product Name</label>
        <input v-model="product.productName" type="text" class="form-control" id="product-name"/>
      </div>
      <div class="form-group">
        <label for="price">Price</label>
        <input v-model="product.price" type="text" class="form-control" id="price"/>
      </div>
      <div class="form-group">
        <label for="quantity">Quantity</label>
        <input v-model="product.quantity" type="text" class="form-control" id="quantity"/>
      </div>
      <button type="submit" class="btn btn-sm btn-success">Add</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "add-product",
  data() {
    return {
      product: {
        id: '',
        productName: "",
        price: '',
        quantity: '',
      },
    };
  },
  methods:{
    handleAdd(){
        this.$emit('add:product',this.product)
    }
  }
};
</script>
<style scoped>
    #addProduct{
        margin-top: 50px;
    }
    .form-group{
        margin: 10px;
    }
    button{
        margin-bottom: 10px;
        margin-left: 10px;
    }
</style>
