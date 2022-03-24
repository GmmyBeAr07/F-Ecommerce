<template>

<section id="Products" style="min-height: 100vh; width: 100%; justify-content: center; flex-direction: column; display: flex; ">

  <div class="container d-flex justify-content-end mb-2 mt-5 pt-3">
    <div class="d-flex w-25 ms-3">
      <label for="" class="form-label">Sort by category
      </label>

      <select
        class="form-select"
        name=""
        id="sortCategory"
        onchange="sortCategory()">
        <option value="All">All</option>
        <option value="Manga">Manga</option>
        <option value="Clothing">Clothing</option>
      </select>
    </div>
  </div>
  <div id="products" class="container d-flex mb-3">
 </div>
</section>
</template>

<script>
export default {
  components: {},
  mounted() {
    let products = JSON.parse(localStorage.getItem("products"))
      ? JSON.parse(localStorage.getItem("products"))
      : [
          {
            title: "Attack On Titan _-_ Vol 1-45",
            category: "Manga",
            price: 249.99,
            img: "https://images5.alphacoders.com/508/508247.jpg",
          },

          {
            title: "Rent A Girlfriend _-_ Vol 12-50",
            category: "Manga",
            price: 179.99,
            img: "https://images4.alphacoders.com/110/1109207.jpg",
          },

          {
            title: "Demon Slayer _-_ TengenUzui Hoodie",
            category: "Clothing",
            price: 279.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202112/bps/product/inc/zwelto1640082717831.jpg",
          },

          {
            title: "Rising Of A Shield Hero _-_ Vol 1-70",
            category: "Manga",
            price: 139.99,
            img: "https://images7.alphacoders.com/981/981840.png",
          },
          {
            title: "Jujutsu Kaisen _-_ White Squad T",
            category: "Clothing",
            price: 229.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202106/bps/product/inc/wrjote1623739390445.jpg",
          },
          {
            title: "Darling In The Franx _-_ White Hoodie",
            category: "Clothing",
            price: 319.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202202/bps/product/inc/llrwxl1646035099901.jpg",
          },

          {
            title: "Demon Slayer _-_ Zenitsu Denim Jacket",
            category: "Clothing",
            price: 359.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202108/bps/product/inc/gbvdaj1629362411097.jpg",
          },

          {
            title: "That Time I Got Reincarnated As A Slime _-_ Vol 21-126",
            category: "Manga",
            price: 269.99,
            img: "https://images.alphacoders.com/119/1193664.jpg",
          },
          {
            title: "(SPECIAL) Chainsaw Man _-_ Full Cllection",
            category: "Manga",
            price: 299.99,
            img: "https://images8.alphacoders.com/118/1183004.jpg",
          },

          {
            title: "Attack On Titan _-_ Levi Tracksuit",
            category: "Clothing",
            price: 369.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202108/bps/product/inc/eddyvz1630410709822.jpg",
          },

          {
            title: "Naruto _-_ NarutoUzumaki Silver Necklace",
            category: "Accessories",
            price: 119.99,
            img: "https://img.fruugo.com/product/8/35/197305358_max.jpg",
          },

          {
            title: "Dragon Ball Z _-_ Android 16 Figurine",
            category: "Accessories",
            price: 259.99,
            img: "https://img.fruugo.com/product/2/20/138082202_max.jpg",
          },

          {
            title: "Dragon Ball Z _-_ Kame Backpack",
            category: "Accessories",
            price: 289.99,
            img: "https://img.fruugo.com/product/3/82/136567823_max.jpg",
          },

          {
            title: "Attack On Titan _-_ Levi Tracksuit",
            category: "Clothing",
            price: 369.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202108/bps/product/inc/eddyvz1630410709822.jpg",
          },

          {
            title: "Tokyo Revengers _-_ Vol 7-50",
            category: "Manga",
            price: 239.99,
            img: "https://images.alphacoders.com/114/1149848.jpg",
          },

          {
            title: "Ranking Of Kings _-_ Vol 1-50",
            category: "Manga",
            price: 179.99,
            img: "https://images3.alphacoders.com/118/1186495.png",
          },

          {
            title: "My Hero Academia _-_ Vol 12-30",
            category: "Manga",
            price: 129.99,
            img: "https://images8.alphacoders.com/736/736903.jpg",
          },

          {
            title: "Spy x Family _-_ Vol 25-70",
            category: "Manga",
            price: 239.99,
            img: "https://images7.alphacoders.com/120/1206753.png",
          },

          {
            title: "Jujutsu Kaisen _-_ Wallet",
            category: "Accessories",
            price: 159.99,
            img: "https://img.fruugo.com/product/9/95/180295959_max.jpg",
          },

          {
            title: "Demon Slayer _-_ (Limited Edition) Tanjiro Oversized T",
            category: "Clothing",
            price: 349.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202202/bps/product/inc/qqbrzu1646033517835.jpg",
          },

          {
            title: "Hunter x Hunter _-_ White T",
            category: "Clothing",
            price: 199.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202108/bps/product/inc/pvnfzp1628826392959.jpg",
          },

          {
            title: "Komi Can't Communicate _-_ Vol 1-30",
            category: "Manga",
            price: 239.99,
            img: "https://images8.alphacoders.com/120/1204612.jpg",
          },

          {
            title: "Demon SLayer _-_ Fox Mask",
            category: "Accessories",
            price: 259.99,
            img: "https://img.fruugo.com/product/5/22/179989225_max.jpg",
          },

          {
            title: "Tokyo Revengers _-_ Mikey Black Hoodie",
            category: "Clothing",
            price: 229.99,
            img: "https://litb-cgis.rightinthebox.com/images/x/202108/bps/product/inc/qefnbt1629362596403.jpg",
          },

          {
            title: "Assassination Classroom _-_ Vol 20-72",
            category: "Manga",
            price: 199.99,
            img: "https://images.alphacoders.com/605/605582.png",
          },

          {
            title: "Teasing Master Takagi-san _-_ Vol 12-90",
            category: "Manga",
            price: 179.99,
            img: "https://images8.alphacoders.com/118/1188996.jpg",
          },

          {
            title: "Jujutsu Kaisen",
            category: "Manga",
            price: 199.99,
            img: "https://images.alphacoders.com/605/605582.png",
          },

          {
            title: "Demon Slayer _-_ Nezuko Figurine",
            category: "Accessories",
            price: 329.99,
            img: "https://img.fruugo.com/product/0/65/190317650_max.jpg",
          },

          {
            title: "Dragon Ball Z _-_ DragonBall Mug",
            category: "Accessories",
            price: 199.99,
            img: "https://img.fruugo.com/product/4/99/135727994_max.jpg",
          },
        ];

    let cart = JSON.parse(localStorage.getItem("cart"))
      ? JSON.parse(localStorage.getItem("cart"))
      : [];

    // READ
    function readProducts(products) {
      document.querySelector("#products").innerHTML = "";
      products.forEach((product, position) => {
        document.querySelector("#products").innerHTML += 

        `<div class="card">
          <img src="${product.img}" class="card-img-top" alt="${product.title}">
          <div class="card-body">
            <h5 class="card-title">${product.title}</h5>
            <p class="card-text">R${product.price}</p>
            <div class="d-flex mb-3">
              <input type="number" class="form-control" value=1 min=1 id="addToCart${position}">
              <button type="button" class="btn btn-secondary ms-3" onclick="addToCart(${position})"><i class="fas fa-cart-plus"></i></button>
            </div>
          </div>

            <div class="d-flex justify-content-end card-footer">
              <button type="button" class="btn btn-secondary me-3" data-bs-toggle="modal" data-bs-target="#editProduct${position}" >
                Change
              </button>

              <button type="button" class="btn btn-secondary me-3" onclick="deleteProduct(${position})" >
                <i class="fa-solid fa-trash"></i>
              </button>
            </div>
        </div>

        <div
          class="modal fade"
          id="editProduct${position}"
          tabindex="-1"
          aria-labelledby="exampleModalLabel"
          aria-hidden="true">

                  <div class="modal-dialog">
                    <div class="modal-content">
                      <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">
                          Change ${product.title}
                        </h5>

                        <button
                          type="button"
                          class="btn-close"
                          data-bs-dismiss="modal"
                          aria-label="Close"></button>
                      </div>

                    <div class="modal-body">
                      <div class="mb-3">
                        <label for="editTitle${position}" class="form-label">Title
                        </label>

                        <input
                          class="form-control"
                          type="text"
                          name="editTitle${position}"
                          id="editTitle${position}"
                          value="${product.title}"/>
                      </div>

                      <div class="mb-3">
                        <label for="editCategory${position}" class="form-label">Category
                        </label>

                        <select
                          class="form-select"
                          name="editCategory${position}"
                          id="editCategory${position}">
                          <option value="All">All</option>
                      <option value="Manga">Manga</option>
                      <option value="Clothing">Clothing</option>
                      <option value="Accessories">Accessories</option>
                        </select>
                      </div>

                      <div class="mb-3">
                        <label for="editPrice${position}" class="form-label">Price
                        </label>

                        <input
                          class="form-control"
                          type="text"
                          name="editPrice${position}"
                          id="editPrice${position}"
                          value="${product.price}"/>
                      </div>

                      <div class="mb-3">
                        <label for="editImg${position}" class="form-label">Image URL
                        </label>

                        <input
                          class="form-control"
                          type="text"
                          name="editImg${position}"
                          id="editImg${position}"
                          value="${product.img}"/>
                      </div>
                    </div>

                    <div class="modal-footer">
                      <button
                        type="button"
                        class="btn btn-secondary"
                        data-bs-dismiss="modal">
                        Close
                      </button>
                      <button
                        type="button"
                        class="btn btn-primary"
                        data-bs-dismiss="modal"
                        onclick="updateProduct(${position})">
                        Save changes
                      </button>
                    </div>
                  </div>
                </div>
              </div>`;
            });
          }

    readProducts(products);
    showCartBadge();

    // CREATE //
    function createProduct() {
      let title = document.querySelector("#addTitle").value;
      let category = document.querySelector("#addCategory").value;
      let price = document.querySelector("#addPrice").value;
      let img = document.querySelector("#addImg").value;

      try {
        if (!title || !price || !img)
          throw new Error("Please fill in all fields");
        products.push({
          title,
          category,
          price,
          img,
        });

        localStorage.setItem("products", JSON.stringify(products));
        readProducts(products);
      }
      
      catch (err) {
        alert(err);
      }
    }

    // UPDATE //
    function updateProduct(position) {
      let title = document.querySelector(`#editTitle${position}`).value;
      let category = document.querySelector(`#editCategory${position}`).value;
      let price = document.querySelector(`#editPrice${position}`).value;
      let img = document.querySelector(`#editImg${position}`).value;

      try {
        if (!title || !price || !img)
          throw new Error("Please fill in all fields");
        products[position] = {
          title,
          category,
          price,
          img,
        };

        localStorage.setItem("products", JSON.stringify(products));
        readProducts(products);
      } 

      catch (err) {
        alert(err);
      }
    }

    // DELETE //
    function deleteProduct(position) {
      let confirmation = confirm(
        "Are you sure you want to delete the selected product?"
      );

      if (confirmation) {
        products.splice(position, 1);
        localStorage.setItem("products", JSON.stringify(products));
        readProducts(products);
      }
    }

    // ADD TO CART //
    function addToCart(position) {
      let qty = document.querySelector(`#addToCart${position}`).value;
      let added = false;
      cart.forEach((product) => {
        if (product.title == products[position].title) {
          alert(
            `You have successfully added ${qty} ${products[position].title} to the cart`
          );

          product.qty = parseInt(product.qty) + parseInt(qty);
          added = true;
        }
      });

      if (!added) {
        cart.push({ ...products[position], qty });
        alert(
          `You have successfully added ${qty} ${products[position].title} to the cart`
        );
      }

      showCartBadge();

      localStorage.setItem("cart", JSON.stringify(cart));
    }

    // Update Cart Badge //
    function showCartBadge() {
      document.querySelector("#badge").innerHTML = cart ? cart.length : "";
    }

    // SORT BY CATEGORY //
    function sortCategory() {
      let category = document.querySelector("#sortCategory").value;

      if (category == "All") {
        return readProducts(products);
      }

      let foundProducts = products.filter((product) => {
        return product.category == category;
      });

      readProducts(foundProducts);
      console.log(foundProducts);
    }

    // SORT BY NAME //
    function sortName() {
      let direction = document.querySelector("#sortName").value;

      let sortedProducts = products.sort((a, b) => {
        if (a.title.toLowerCase() < b.title.toLowerCase()) {
          return -1;
        }

        if (a.title.toLowerCase() > b.title.toLowerCase()) {
          return 1;
        }

        return 0;
      });

      if (direction == "descending") sortedProducts.reverse();
      console.log(sortedProducts);
      readProducts(products);
    }

    // SORT BY PRICE //
    function sortPrice() {
      let direction = document.querySelector("#sortPrice").value;

      let sortedProducts = products.sort((a, b) => a.price - b.price);

      console.log(sortedProducts);

      if (direction == "descending") sortedProducts.reverse();
      readProducts(sortedProducts);
    }
  },
};
</script>

<style>
#products {
  flex-wrap: wrap;
  gap: 20px;
}

img {
  height: 200px !important;
  object-fit: cover;
}

.card {
  width: calc((100% / 4) - 15px);
  min-width: 300px;
  margin-bottom: 150px;
}

.card-title {
  text-transform: capitalize;
}

#Products {
    background:linear-gradient(0deg, rgba(42, 87, 13, 0.062), rgba(59, 83, 20, 0.315)), url('../images/Landing.jpg'); 
    background-repeat: no-repeat;
    background-attachment: fixed; 
    backface-visibility:visible;
    background-size: cover;
  }
</style>
