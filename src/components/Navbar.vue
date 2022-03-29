<template>

  <!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-light bg-light">

  <!-- Container wrapper -->
  <div class="container">

    <!-- Toggle button -->
    <button
      class="navbar-toggler"
      type="button"
      data-mdb-toggle="collapse"
      data-mdb-target="#navbarButtonsExample"
      aria-controls="navbarButtonsExample"
      aria-expanded="false"
      aria-label="Toggle navigation">
      <i class="fas fa-bars"></i>
    </button>

    <!-- Collapsible wrapper -->
    <div class="collapse navbar-collapse" id="navbarButtonsExample">

      <!-- Left links -->
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item" >

 <a class="navbar-brand" href="/">So you're a WEEB?
    </a>

        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation">
          <span class="navbar-toggler-icon">
          </span>
        </button>

      <router-link class="btn btn-primary me-3" style="background: #0d6efd" @click="toggleNav" :to="{ name: 'Products' }">
      Products
    </router-link>
  </li>
</ul>

      <div class="collapse navbar-collapse justify-content-end"
              id="navbarSupportedContent">
          <ul class="navbar-nav mb-2 mb-lg-0 mr-auto">
            <li class="nav-item">
              <a
                class="btn btn-primary me-3"
                aria-current="page"
                href="/">Home
              </a>
            </li>

            <li class="nav-item">
              <a
                class="btn btn-primary active position-relative"
                href="./views/Home.vue">Cart
                <span
                  id="badge"
                  class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger"></span></a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav> 
</template>

<script>
export default {
  data() {
    return {
      isActive: false,
    };
  },
  
  methods: {
    toggleNav() {
      this.isActive = !this.isActive;
    },
    
    logout() {
      localStorage.clear();
      this.toggleNav;
    },
  },
};
</script>


<style lang="scss" scoped>
 .sticky {
   position: fixed;
   top: 0;
   width: 100%;
 }

#nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 10%;
  background: #5f79c22d;
}

#nav-btn {
  position: fixed;
  z-index: 1030;
  top: 20px;
  right: 20px;
  background: #ffffff;

  padding: 20px;

  border-radius: 50%;
  border: none;
  outline: none;
  display: none;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #ffffff;
    padding: 20px;
    text-decoration: none;
    &.router-link-exact-active:not(.logout) {
    color: rgba(57, 65, 182, 0.931);
    }
  }
}

@media screen and (max-width: 800px) {
  #nav {
    height: 100%;
    left: -100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: left 0.1s linear;
  }
  #nav.active {
    left: 0;
  }
  #nav-btn {
    display: block;
  }
}
</style>
