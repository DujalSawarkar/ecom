<template>
  <div class="add-category">
    <h1>Add Category</h1>
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="image">Image URL:</label>
        <input type="text" id="image" v-model="categoryData.image" required />
      </div>
      <div class="form-group">
        <label for="name">Category Name:</label>
        <input type="text" id="name" v-model="categoryData.name" required />
      </div>
      <button type="submit">Add Category</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

// Reactive variable to store category data
const categoryData = ref({
  image: "",
  name: "",
});

// Handle form submission
const handleSubmit = async () => {
  try {
    // Make a POST request to submit the category data
    const response = await $fetch("http://localhost:4000/user/category", {
      method: "POST",
      body: {
        name: categoryData.value.name,
        image: categoryData.value.image,
      },
    });
    console.log(categoryData.value);
  } catch (error) {
    console.error("Error adding category:", error);
  }
};

// Function to reset the form fields after submission
const resetForm = () => {
  categoryData.value.image = "";
  categoryData.value.name = "";
};
</script>

<style scoped>
.add-category {
  height: 100vh;
  margin: 0 auto;
  padding: 15% 30%;
}

.form-group {
  margin-bottom: 20px;
}

input[type="text"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
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
