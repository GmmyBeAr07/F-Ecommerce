<template>
  <section
    id="Landing" 
    style=" min-height: 91.6vh;
            width: 100%;
            justify-content: center;
            flex-direction: column;
            display: flex;">

    <div class="w3-container w3-center w3-animate-top">
      <span class="h1"><h1>Anime Xclusive</h1></span>
      <span class="h2"><h2></h2> Manga, Clothing, Accessories...We Got You</span>

      <br>

      <a class="signin" href="../register">Sign Up</a>

      <a class="login" href="../login">Login</a>
    </div>
    <section class="">

  <!-- Footer -->
  <footer class="text-center text-white" style="background-color: rgba(105, 121, 192, 0.801);">
    
    <div class="container p-4 pb-0">

      <section class="">
        <p class="d-flex justify-content-center align-items-center;">
          <span class="me-3">Join Us Today For All The New Anime Merch and Manga Drops</span>
        </p>

            © 2022 Copyright:


        <a class="btn btn-dark px-4"
           href="https://github.com/GmmyBeAr07?tab=repositories"
           role="button" target="_blank">
          <i class="fab fa-github" >
          </i>
        </a>
      </section>
    </div>
  </footer>
</section>
</section>
</template>

<script>
export default {
  name: "Landing",
  props: {
    msg: String,
  },
};
</script>

<style scoped>

.landingbuttons {
  color: rgb(97, 95, 173);
}

footer {
  position: absolute;
  background: rgb(57, 79, 141);
  bottom: 0;
  width: 100%;
  height: 14%;
}

#Landing {
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.384), rgba(0, 0, 0, 0.397)),
  url("../images/Register.jpg");
  background-repeat: no-repeat;
  background-attachment: fixed;
  backface-visibility: visible;
  background-size: 100% 100%;
}
</style>
