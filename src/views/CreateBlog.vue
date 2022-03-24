<template>

<section id="CP" style="min-height: 100vh; width: 100%; justify-content: center; flex-direction: column; display: flex;">


  <form @submit.prevent="createBlog" class="form neu-border">
    <h2 class="form-heading">Add an Item</h2>
    <input
      class="form-input neu-border-inset"
      type="text"
      v-model="title"
      placeholder="Item"
      required/>
 
    <input class="form-input neu-border-inset"
            type="text"
            v-model="img"
            placeholder="Item Image"
            required/>
 
    <textarea class="form-input neu-border-inset"
            type="text"
            v-model="body"
            placeholder="Price"
            required>
      </textarea>
 
    <button type="submit" class="form-btn neu-border">Add Product</button>
  </form>
</section>
</template>
<script>
export default {
  data() {
    return {
      title: "",
      body: "",
      img: "",
    };
  },
  
  methods: {
    createBlog() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      
      fetch("https://full-proj.herokuapp.com/", {
        method: "POST",
        body: JSON.stringify({
          title: this.title,
          body: this.body,
          img: this.img,
        }),
        
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
      
        .then((response) => response.json())
        .then((json) => {
          alert("Post Created");
          this.$router.push({ name: "Products" });
        })
        
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>

<style>

#CP {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.534), rgba(0, 0, 0, 0.733)), url('../images/Landing.jpg'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }

.neu-border {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #5e5a9c, -8px -8px 15px #ffffffbe;
}
.neu-border-inset {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #5868c2, -8px -8px 15px #ffffffbe;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 40px;
  gap: 20px;
  width: 100%;
  max-width: 600px;
  margin-inline: auto;
}

.form-heading {
  text-align: center;
  text-transform: uppercase;
}

.form-input,
.form-btn {
  border: none;
  outline: none;
  padding: 20px;
}

.form-btn {
  cursor: pointer;
  transition: all 0.1s linear;
}

.form-btn:hover {
  transform: scale(1.05);
}

.form-social-login {
  display: flex;
  justify-content: space-between;
}

.form-social-btn {
  width: 45%;
  color: rgb(160, 79, 79);
}
</style>
