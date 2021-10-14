<template>
  <div id="product-table">
    <div v-if="!products.length" class="alert alert-info" role="alert">
      No se han agregado productos
    </div>
    <table class="table">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Descripción</th>
          <th>Precio</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(product, index) in products" :key="index">
          <td v-if="editIndex === index">
            <input
              v-model="editableProduct.name"
              type="text"
              class="form-control"
            />
          </td>
          <td v-else>{{ product.name }}</td>
          <td v-if="editIndex === index">
            <input
              v-model="editableProduct.description"
              type="text"
              class="form-control"
            />
          </td>
          <td v-else>{{ product.description }}</td>
          <td v-if="editIndex === index">
            <input
              v-model="editableProduct.price"
              type="number"
              class="form-control"
            />
          </td>
          <td v-else>${{ product.price }}</td>
          <td>
            <button
              class="btn btn-info ml-2"
              @click="editProduct(product, index)"
            >
              Editar
            </button>
            <button
              class="btn btn-danger"
              @click="$emit('delete-product', index)"
            >
              Eliminar
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "product-table",
  props: {
    products: {
      type: Array,
      default: () => [],
    },
  },
};
</script>