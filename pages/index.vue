<template>
  <div class="main-div">
    <div
      v-for="(category, index) in category"
      :key="index"
      class="category-Div"
    >
      <img :src="category.imgUrl" alt="img" class="Image" />
      <p>{{ category.name }}</p>
    </div>
    <!-- <ul v-for="(categoryname, index) in category" :key="index">
      <li>{{ categoryname }}</li>
    </ul> -->
  </div>
  <nuxt-link to="/category"><button>category</button></nuxt-link>
</template>

<script>
export default {
  data() {
    return {
      category: [
        {
          id: 1,
          name: "name1",
          imgUrl: "https://dummyimage.com/sqrpop",
        },
        {
          id: 2,
          name: "name2",
          imgUrl: "https://dummyimage.com/sqrpop",
        },
        {
          id: 3,
          name: "name3",
          imgUrl: "https://dummyimage.com/sqrpop",
        },
      ],
    };
  },
};
</script>

<style scoped>
.main-div {
  height: 80vh;
  width: 80%;
  margin: auto;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

.category-Div {
  border: 1px solid black;

  /* width: 30%; */
}

button {
  margin-left: 45%;
  font-size: 20px;
  padding: 1%;
}
</style>
