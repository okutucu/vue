<template>
    <div id="Add">
      <h3>Ürün Ekleme Formu</h3>

      <div>
          <form @submit.prevent="handleAdd">
            <div class="row">
              <div class="col-md-4 form-group">
                <label for="productName">Ürün İsmi</label>
                <input type="text" v-model="product.productName" id="productName" class="form-control" placeholder="Lütfen ürün ismi giriniz..">
              </div>
              <div class="col-md-4 form-group">
                <label for="productCategory">Kategori Bilgisi</label>
                <input type="text" v-model="product.productCategory" id="productCategory" class="form-control" placeholder="Lütfen kategori bilgisi giriniz..">
              </div>
              <div class="col-md-4 form-group">
                <label for="productDescription">Ürün açıklaması </label>
                <input type="text" v-model="product.productDescription" id="productDescription" class="form-control" placeholder="Lütfen ürün açıklaması giriniz..">
              </div>
              <div class="col-md-4 form-group">
                <label for="productPrice">Ürün fiyatı </label>
                <input type="text" v-model="product.productPrice" id="productPrice" class="form-control" placeholder="Lütfen ürün fiyatını giriniz..">
              </div>
              <div class="col-md-4 form-group">
                <label for="productInStock">Stok sayısı</label>
                <input type="text" v-model="product.productInStock" id="productInStock" class="form-control" placeholder="Lütfen stok sayısını giriniz..">
              </div>
            </div>
            <button type="submit" class="btn btn-lg btn-success mt-3">Ekle</button>


          </form>

      </div>

    </div>
</template>

<script>
export default {
  name: "ProductAdd",
  data(){
    return {
      product:{
        id:'',productName:'',productCategory:'', productDescription:'',productPrice:'',productInStock:''

      }
    }
  },
  methods:{
    handleAdd(){
      this.$emit("add:product",this.product)
    }
  }
}
</script>



<style scoped>
#Add{
  margin: 100px;
}
</style>