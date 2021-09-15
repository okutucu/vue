<template>
  <div id="list">
    <h3>Ürünler Listesi</h3>
    <p v-if="products.length===0">Ürün listesi boş</p>
    <table v-else class="table">
      <thead>
      <tr>
        <th>Ürün Id</th>
        <th>Ürün İsmi</th>
        <th>Ürün Categorisi</th>
        <th>Ürün Açıklaması</th>
        <th>Ürün Fiyatı</th>
        <th>Ürün Stok Sayısı</th>
        <th></th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="product in products" :key="product.id">

        <td v-if="updateId ===product.id">
          <input type="text" v-model="product.id" class="form-control" id="id">
        </td>
        <td v-else>{{product.id}}</td>
        <td v-if="updateId ===product.id">
          <input type="text" v-model="product.productName" class="form-control" id="productName">
        </td>
        <td v-else>{{product.productName}}</td>
        <td v-if="updateId ===product.id">
          <input type="text" v-model="product.productCategory" class="form-control" id="productCatagory">
        </td>
        <td v-else>{{product.productCategory}}</td>
        <td v-if="updateId ===product.id">
            <input type="text" v-model="product.productDescription" class="form-control" id="productDescription">
        </td>
        <td v-else>{{product.productDescription}}</td>
        <td v-if="updateId ===product.id">
          <input type="text" v-model="product.productPrice" class="form-control" id="productPrice">
        </td>
        <td v-else>{{product.productPrice}}</td>
        <td v-if="updateId ===product.id">
          <input type="text" v-model="product.productInStock" class="form-control" id="productInStock">
        </td>
        <td v-else>{{product.productInStock}}</td>
        <td v-if="updateId!==product.id">
          <button class="btn btn-primary btn-sm me-2" @click="handleUpdate(product)">Güncelle</button>
          <button class="btn btn-danger btn-sm" @click="handleDelete(product)">Sil</button>
        </td>
        <td v-else>
          <button class="btn btn-success btn-sm me-2" @click="handleSave(product)">Kaydet</button>
          <button class="btn btn-warning btn-sm" @click="updateId=null">İptal</button>
        </td>


      </tr>
      </tbody>


    </table>

  </div>

</template>

<script>
export default {
  name: "ProductList",
  data(){
    return{
      updateId:null
    };
  },
  props:{
    products:Array
  },

  methods:{
    handleDelete(product){
      this.$emit("delete:product",product)
    },
    handleUpdate(product){
      this.updateId =product.id
    },
    handleSave(product){
      this.$emit("update:product",product)
      this.updateId =null
    }
  }
}
</script>

<style scoped>
#list{
  margin: 100px;
}
</style>