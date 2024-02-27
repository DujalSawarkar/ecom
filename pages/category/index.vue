<template>
  <div>
    <h1>Category Page</h1>
    <div class="main-div">
      <div
        v-for="(category, index) in category"
        :key="index"
        class="category-Div"
      >
        <img
          src="https://thumbs.dreamstime.com/b/electronics-store-flat-design-long-shadow-glyph-icon-household-equipment-online-shop-category-small-major-domestic-appliance-187368856.jpg"
          alt="img"
          class="Image"
        />
        <nuxt-link :to="`/category/${category.name}`">
          <p>{{ category.name }}</p>
        </nuxt-link>
      </div>
    </div>
    <nuxt-link to="category/add"
      ><button class="btn">Add Category</button></nuxt-link
    >
  </div>
</template>

<script setup>
const { data: category } = useFetch(
  () => "http://localhost:4000/user/category"
);
</script>

<style scoped>
* {
  text-decoration: none;
}
.main-div {
  height: 80vh;
  width: 80%;
  margin: auto;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

.category-Div {
  height: 300px;
  border: 1px solid black;
  border-radius: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  /* width: 30%; */
}

.Image {
  height: 200px;
  border-radius: 20px;
}

p {
  color: black;
  font-size: 29px;
  /* padding: 18%; */
}

.btn {
  margin-left: 45%;
  font-size: 20px;
  padding: 1%;
}
.btn:hover {
  cursor: pointer;
}
</style>
