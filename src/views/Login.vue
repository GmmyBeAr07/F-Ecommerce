<template>

<section id="Login" style="min-height: 100vh; min-width: 100vh; justify-content: center; flex-direction: column; display: flex;">

  <form @submit.prevent="login" class="form neu-border">
    <h2 class="form-heading">Sign Up</h2>
    <input
      class="form-input neu-border-inset"
      type="email"
      v-model="email"
      placeholder="Email"/>

    <input
      class="form-input neu-border-inset"
      type="password"
      v-model="password"
      placeholder="Password"/>

    <a href="/Products"> Login</a>

    <p> 
      <router-link :to="{ name: 'Register' }">Create an account</router-link>
    </p>
  </form>
</section>
</template>

<script>
export default {

  name: "register",
  props: ["baseURL"],
  data() {
    return {
      username: "",
      email: "",
      password: "",
      isAdmin: false,
    };
  },
  
  methods: {
    register() {
      console.log("Register Success");
      const person = {
        username: this.username,
        email: this.email,
        password: this.password,
      };

      console.log(person);
      fetch("https://thurs-social-media.herokuapp.com/api/auth/", {
        method: "POST",
        body: JSON.stringify(person),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
        // mode: "no-cors"
      })
        .then((response) => response.json())
        .then((json) => {
          console.log(json);
          alert("User registered");
          localStorage.setItem("jwt", json.jwt);
          this.$router.push({ name: "Login" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>


<style>
#Login {
    background:linear-gradient(0deg, rgba(0, 0, 0, 0.39), rgba(0, 0, 0, 0.534)), url('../images/Products.jpg'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: 100% 100%;
  }

.neu-border {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #000000, -8px -8px 15px #ffffffbe;
}

.neu-border-inset {
  border-radius: 30px;
  background: #f5f5f55e;
  box-shadow: 8px 8px 15px #4f91bd, -8px -8px 15px #ffffffbe;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: right;
  padding: 40px;
  gap: 20px;
  width: 50%;
  margin-inline: auto;
  max-width: 600px;
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
  color: #333;
}
</style>
