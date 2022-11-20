<template>
    <div class="container">
        <h3>Product List</h3>
        <br>
        <p v-if="products.length==0">There is no product !!</p>
        <table v-else class="table border">
            <thead>
                <tr>
                    <th>Id</th>
                    <th>Product Name</th>
                    <th>Price</th>
                    <th>Quantity</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="product in products" :key="product.id">

                    <td>{{product.id}}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.productName" type="text" class="form-control" id="product-name">
                    </td>
                    <td v-else>{{product.productName}}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.price" type="text" class="form-control" id="price">
                    </td>
                    <td v-else>{{product.price}}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.quantity" type="text" class="form-control" id="quantity">
                    </td>
                    <td v-else>{{product.quantity}}</td>
                                        
                    <td v-if="updateId != product.id">
                        <button class="btn btn-sm btn-primary" @click="handleUpdate(product)">update</button>
                        <button class="btn btn-sm btn-danger" @click="handleDelete(product)">delete</button>
                    </td>
                    <td v-else>
                        <button class="btn btn-sm btn-primary" @click="handleSave(product)">save</button>
                        <button class="btn btn-sm btn-danger" @click="handleCancel()">cancel</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    name: "product-list",
    data(){
        return{
            updateId: null
        }
    },
    props:{
        products: Array
    },
    methods:{
         handleDelete(product){
            this.$emit("delete:product",product)
        },
        handleUpdate(product){
            this.updateId = product.id
        },
        handleSave(product){
            this.$emit("save:product",product)
            this.updateId = null
            //console.log(product)
        },
        handleCancel(){
            this.updateId = null
        }
    }
}
</script>

<style scoped>

</style>