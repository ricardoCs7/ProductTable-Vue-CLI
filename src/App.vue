<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12"><h1>Productos</h1></div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <product-form @add-product="addProduct" />
        <product-table :products="products" @delete-product="deleteProduct" />
      </div>
    </div>
  </div>
</template>



<script>
import ProductTable from "@/components/ProductTable.vue";
import ProductForm from "@/components/ProductForm.vue";
export default {
  name: "app",
  components: { ProductTable, ProductForm },
  data() {
    return {
      editableProduct: {},
      editIndex: -1,
      products: [
        { name: "Uranio", description: "Para uso casero", price: 500 },
        { name: "Unicornio", description: "3 cuernos", price: 600 },
        {
          name: "Dinosaurio",
          description: "Velociraptor 5 metros",
          price: 340,
        },
      ],
    };
  },
  methods: {
    editProduct(product, index) {
      this.editableProduct = Object.assign({}, product);
      this.editableProduct = { ...product };
      this.editIndex = index;
    },
    addProduct(product) {
      this.products = [...this.products, product];
    },
    deleteProduct(index) {
      this.products.splice(index, 1);
    },
  },
};
</script>


