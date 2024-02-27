<template>
  <div class="add-product">
    <h1>Add Product</h1>
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="image">Image URL:</label>
        <input type="text" id="image" v-model="productData.image" required />
      </div>
      <div class="form-group">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="productData.name" required />
      </div>
      <div class="form-group">
        <label for="price">Price:</label>
        <input type="number" id="price" v-model="productData.price" required />
      </div>
      <div class="form-group">
        <label for="description">Description:</label>
        <textarea
          id="description"
          v-model="productData.description"
          required
        ></textarea>
      </div>
      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
// import axios from "axios";

// Reactive variable to store product data
const productData = ref({
  image: "",
  name: "",
  price: "",
  description: "",
});

// Handle form submission
const handleSubmit = async () => {
  try {
    // Make a POST request to submit the category data
    const response = await $fetch("http://localhost:4000/user/products", {
      method: "POST",
      body: {
        image: productData.value.image,
        name: productData.value.name,
        price: productData.value.price,
        description: productData.value.description,
      },
    });
    console.log(productData.value);
  } catch (error) {
    console.error("Error adding category:", error);
  }
};

// Function to reset the form fields after submission
const resetForm = () => {
  productData.value.image = "";
  productData.value.name = "";
  productData.value.price = "";
  productData.value.description = "";
};
</script>

<style scoped>
.add-product {
  max-width: 600px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 20px;
}

input[type="text"],
input[type="number"],
textarea {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

textarea {
  height: 100px;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
