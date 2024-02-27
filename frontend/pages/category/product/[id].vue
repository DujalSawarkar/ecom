<script setup>
// const data = {
//   id: 1,
//   name: "Shirt",
//   imgUrl: "https://dummyimage.com/sqrpop",
//   dis: "hurry up....upto 10% discount",
//   category: "Shirt",
//   price: 200,
// };

const route = useRoute();
const { data: data } = useFetch(
  () => `http://localhost:4000/user/products/${route.params.id}`
);

console.log(data);
</script>
<template>
  <div class="Main-div">
    <!-- <p>{{ route.params.id }}</p> -->
    <div class="info-div">
      <img :src="data.image" alt="#" class="image" />

      <div>
        <h1>{{ data.name }}</h1>
        <h3>Price : ${{ data.price }}</h3>
        <!-- <h3>Category : {{ data.category }}</h3> -->
        <p class="description">{{ data.discription }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.Main-div {
  height: 80vh;
  width: 80%;
  margin: auto;
}

.info-div {
  margin-top: 5%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  border: 1px solid black;
  border-radius: 20px;
  padding: 5%;
  gap: 5rem;
}

.image {
  height: 400px;
  widows: 400px;
  border-radius: 20px;
}
h1 {
  font-size: 60px;
}
h3 {
  font-size: 30px;
}
.discription {
  font-size: 20px;
}
</style>
