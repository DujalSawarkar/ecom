<script setup>
// const { name } = useRoute().params;
const route = useRoute();
const { data: category } = useFetch(
  () => `http://localhost:4000/user/products/category/${route?.params?.id}`
);

// console.log("res : ", category, route.params.id);
</script>
<template>
  <div class="Container">
    <div
      v-for="(category, index) in category"
      class="Container-div"
      :key="index"
    >
      <nuxt-link :to="`product/${category.id}`">
        <div class="info">
          <img :src="category.image" alt="#" class="image-div" />
          <div class="info-inner">
            <h1>{{ category.name }}</h1>
            <h3>Price : ${{ category.price }}</h3>
            <!-- <h3>Category : {{ category.category }}</h3> -->
            <p class="description">{{ category.discription }}</p>
          </div>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<style>
.Container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  /* align-items: center; */
  margin: 10%;
  gap: 50px;
}

/* Each individual item */
.Container-div {
  max-width: 300px; /* Adjust the max-width as needed */
  border: 1px solid #ccc;
  border-radius: 5px;
  overflow: hidden; /* Ensure contents don't overflow */
  transition: transform 0.3s ease;
  display: flex;
  justify-content: center;
  align-items: center;
}

.Main-div:hover {
  transform: translateY(-5px);
}

.image-div {
  height: 300px;
  width: 300px;
  /* height: auto; */
  display: block;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.info {
  padding: 15px;
}
.info-inner {
  padding: 5%;
}
.info-inner h1 {
  font-size: 20px;
  margin-bottom: 10px;
}

.info-inner h3 {
  font-size: 16px;
  margin-bottom: 5px;
}

.description {
  font-size: 14px;
  line-height: 1.5;
}
</style>
