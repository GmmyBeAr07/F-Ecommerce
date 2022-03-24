<template>
  <div v-if="products">
    <h2>Products</h2>
    <div class="products-container" v-if="products">
      <router-link
        v-for="product of products"
        :key="product._id"
        :to="{ name: 'ProductDetails', params: { id: product._id } }">
        <img :src="product.img" :alt="product.title" />
        {{ product.author_name }}
      </router-link>
    </div>
  </div>

   <div v-else>Loading Item...
 </div>
</template>

<script>
export default {
  data() {
    return {
      products: null,
    };
  },

  mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("https://full-proj.herokuapp.com/", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })

        .then((response) => response.json())
        .then((json) => {
          this.products = json;
          this.products.forEach(async (product) => {
            await fetch(
              "https://full-proj.herokuapp.com/" + product.author,
              {
                method: "GET",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                },
              }
            )

              .then((response) => response.json())
              .then((json) => {
                product.author_name = json.name;
              });
          });
        })

        .catch((err) => {
          alert("User not logged in");
        });

    } else {
      alert("User not logged in");
      this.$router.push({ name: "Login" });
    }},
};
</script>

<style>
#blogs {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.555), rgba(0, 0, 0, 0.74)), url('../images/Register.jpg'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }

.blogs-container {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  margin-inline: auto;
  padding: 30px;
  gap: 2%;
  justify-content: stretch;
  align-items: stretch;
  flex-direction: column;
}

img {
  max-width: 50vw;
}
</style>
