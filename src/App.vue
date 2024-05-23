<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-custom text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="../src/assets/logogitar.jpeg" />
          </q-avatar>
          Music Instrument Store
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/page1" label="Instrument Music Shop" />
        <q-route-tab to="/page2" label="Singing Supplies Store" />
      </q-tabs>
    </q-header>
    <q-drawer
      show-if-above
      v-model="leftDrawerOpen"
      side="left"
      bordered
      class="drawer-style"
    >
      <!-- Menu card content -->
      <q-card class="q-mt-md">
        <q-card-section>
          <div class="menu-title">Menu</div>
        </q-card-section>

        <q-list>
          <!-- Menu Item 1 -->
          <q-item clickable v-ripple class="menu-item">
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="home" />
            </q-item-section>
            <q-item-section class="menu-item-text"> Home </q-item-section>
          </q-item>

          <!-- Menu Item 2 -->
          <q-item clickable v-ripple class="menu-item">
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="music_note" />
            </q-item-section>
            <q-item-section class="menu-item-text">
              Instruments
            </q-item-section>
          </q-item>

          <!-- Menu Item 3 -->
          <q-item clickable v-ripple class="menu-item">
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="star" />
            </q-item-section>
            <q-item-section class="menu-item-text"> Offers </q-item-section>
          </q-item>

          <!-- Menu Item 4 -->
          <q-item clickable v-ripple class="menu-item">
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="info" />
            </q-item-section>
            <q-item-section class="menu-item-text"> About Us </q-item-section>
          </q-item>
        </q-list>
      </q-card>

      <!-- Submenu at the bottom -->
      <q-card class="q-mt-md">
        <q-card-section>
          <div class="menu-title">Settings</div>
        </q-card-section>
        <q-list>
          <q-item class="submenu-item" clickable v-ripple>
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="person" />
            </q-item-section>
            <q-item-section class="submenu-item-text"> Profile </q-item-section>
          </q-item>
          <q-item class="submenu-item" clickable v-ripple>
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="tune" />
            </q-item-section>
            <q-item-section class="submenu-item-text">
              Preferences
            </q-item-section>
          </q-item>
          <q-item class="submenu-item" clickable v-ripple>
            <q-item-section avatar class="menu-item-icon">
              <q-icon name="security" />
            </q-item-section>
            <q-item-section class="submenu-item-text">
              Security
            </q-item-section>
          </q-item>
        </q-list>
      </q-card>
    </q-drawer>

    <q-page-container class="container-style">
      <router-view />
      <div class="q-pa-md">
        <q-carousel
          arrows
          animated
          v-model="slide"
          height="400px"
          class="carousel-style"
        >
          <q-carousel-slide
            name="first"
            img-src="./assets/backgroundcarosel1.jpg"
          >
            <div class="absolute-bottom custom-caption">
              <div class="text-h2">All yours instrument music</div>
              <div class="text-subtitle1">Music</div>
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="second" img-src="./assets/Slide2.jpg">
            <div class="absolute-bottom custom-caption">
              <div class="text-h2"></div>
              <div class="text-subtitle1">People's Choice in Music</div>
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="third" img-src="./assets/slideee.jpg">
            <div class="absolute-bottom custom-caption">
              <div class="text-h2"></div>
              <div class="text-subtitle1">All Your Music Needs Are Here</div>
            </div>
          </q-carousel-slide>
        </q-carousel>

        <!-- Product Section -->
        <div class="product-section">
          <q-banner class="q-my-md">
            <template v-slot:avatar>
              <q-icon name="star" />
            </template>
            Special Offer on Guitars!
          </q-banner>

          <q-banner class="q-my-md">
            <template v-slot:avatar>
              <q-icon name="star" />
            </template>
            New Arrivals in Drums!
          </q-banner>

          <div class="q-gutter-md">
            <q-card
              class="my-card"
              v-for="product in products"
              :key="product.id"
            >
              <q-img
                :src="product.image"
                :alt="product.name"
                class="product-image"
              />
              <q-card-section>
                <div class="product-title">{{ product.name }}</div>
                <div class="product-description">{{ product.description }}</div>
              </q-card-section>
              <q-card-actions align="right">
                <q-btn flat label="Details" @click="viewDetails(product.id)" />
                <q-btn
                  flat
                  label="Add to Cart"
                  color="primary"
                  @click="addToCart(product)"
                />
              </q-card-actions>
            </q-card>
          </div>
        </div>
      </div>
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar class="begrounfoter">
        <q-toolbar-title class="backgroundfooter">
          <q-avatar>
            <img src="../src/assets/logogitar.jpeg" />
          </q-avatar>
          <div>Music Instrument Store</div>
        </q-toolbar-title>
        <div class="footer-content">
          <div class="footer-section">
            <div class="footer-title">Contact Us</div>
            <div class="footer-item">
              <q-icon name="person" class="footer-icon" />
              <span>Yudha Dwi Darmawan</span>
            </div>
            <div class="footer-item">
              <q-icon name="email" class="footer-icon" />
              <span>yudhadwidarmawan@gmaill.com</span>
            </div>
            <div class="footer-item">
              <q-icon name="whatsapp" class="footer-icon" />
              <span>+62895633883</span>
            </div>
          </div>
        </div>
      </q-toolbar>
    </q-footer>

    <!-- Checkout Modal -->
    <q-dialog v-model="checkoutDialog">
      <q-card>
        <q-card-section>
          <div class="text-h6">Checkout</div>
        </q-card-section>

        <q-card-section>
          <div v-for="item in cart" :key="item.id">
            <div>{{ item.name }} - {{ item.description }}</div>
          </div>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn
            flat
            label="Close"
            color="primary"
            @click="checkoutDialog = false"
          />
          <q-btn
            flat
            label="Proceed to Payment"
            color="primary"
            @click="proceedToPayment"
          />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const rightDrawerOpen = ref(false);
    const slide = ref("first");
    const checkoutDialog = ref(false);
    const cart = ref([]);

    const products = ref([
      {
        id: 1,
        name: "Guitar",
        description: "High-quality acoustic guitar",
        image: "../src/assets/guitar.jpeg",
      },
      {
        id: 2,
        name: "Drum Set",
        description: "Complete drum set with cymbals",
        image: "../src/assets/drum.jpeg",
      },
      {
        id: 3,
        name: "piano",
        description: "Electronic keyboard with 88 keys",
        image: "../src/assets/piano.jpeg",
      },
      {
        id: 4,
        name: "Clarinet",
        description: "High Quality and the best product",
        image: "../src/assets/clarinet.jpeg",
      },
      {
        id: 5,
        name: "Cello",
        description: "High Quality and the best product",
        image: "../src/assets/cello.jpeg",
      },
      {
        id: 6,
        name: "Harp",
        description: "High Quality and the best product",
        image: "../src/assets/harp.jpeg",
      },
      {
        id: 7,
        name: "Violin",
        description: "High Quality and the best product",
        image: "../src/assets/violin.jpeg",
      },
      {
        id: 8,
        name: "Trompet",
        description: "High Quality and the best product",
        image: "../src/assets/trompet.jpeg",
      },
      {
        id: 9,
        name: "Saxophone",
        description: "High Quality and the best product",
        image: "../src/assets/saxophone.jpeg",
      },
      {
        id: 10,
        name: "Flute",
        description: "High Quality and the best product",
        image: "../src/assets/flute.jpg",
      },
      {
        id: 11,
        name: "Electric Guitar",
        description: "High Quality and the best product",
        image: "../src/assets/electricgitar.jpg",
      },
      {
        id: 12,
        name: "Ukulele",
        description: "High Quality and the best product",
        image: "../src/assets/ukulele.jpeg",
      },
    ]);

    const viewDetails = (id) => {
      console.log("View details for product", id);
    };

    const addToCart = (product) => {
      cart.value.push(product);
      checkoutDialog.value = true;
    };

    const proceedToPayment = () => {
      console.log("Proceed to payment with items", cart.value);
      checkoutDialog.value = false;
    };

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      rightDrawerOpen,
      toggleRightDrawer() {
        rightDrawerOpen.value = !rightDrawerOpen.value;
      },
      slide,
      products,
      viewDetails,
      addToCart,
      checkoutDialog,
      cart,
      proceedToPayment,
    };
  },
};
</script>

<style scoped>
.custom-caption {
  text-align: center;
  padding: 12px;
  color: white;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.bg-custom {
  background-color: #191970 !important;
}

.container-style {
  padding: 16px;
  background-color: #f5f5f5;
}

.carousel-style {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.drawer-style {
  background-color: #f0f0f0;
  padding: 16px;
}

.q-carousel-slide img {
  object-fit: cover;
  transition: transform 0.5s ease;
}

.q-carousel-slide img:hover {
  transform: scale(1.05);
}

.product-section {
  margin-top: 32px;
}

.my-card {
  width: 300px;
  margin: 16px;
  display: inline-block;
  vertical-align: top;
}

.product-image {
  height: 200px;
  object-fit: cover;
}

.q-banner {
  background-color: #ffd700 !important;
  color: #000;
  border-radius: 8px;
}

.product-title {
  font-size: 18px;
  font-weight: bold;
  margin-top: 8px;
}

.product-price {
  font-size: 16px;
  color: #007bff;
  margin-top: 4px;
}

.product-description {
  font-size: 14px;
  margin-top: 8px;
}

.btn {
  display: inline-block;
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  text-decoration: none;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #0056b3;
}

.sale-tag {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 5px 10px;
  background-color: #ff4500;
  color: #fff;
  font-size: 12px;
  border-radius: 5px;
}

.bg-grey-8 {
  background-color: #303030 !important;
}

.text-white {
  color: #fff !important;
}
.drawer-style {
  background-color: #ffffff;
  padding: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.q-mt-md {
  margin-top: 16px;
}

.menu-title {
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

.menu-item {
  display: flex;
  align-items: center;
  padding: 12px 16px;
  border-bottom: 1px solid #e0e0e0;
  transition: background-color 0.3s;
}

.menu-item:hover {
  background-color: #f9f9f9;
}

.menu-item-icon {
  margin-right: 12px;
  color: #007bff;
}

.menu-item-text {
  font-size: 16px;
  color: #555;
}

.submenu {
  margin-left: 24px;
}

.submenu-item {
  display: flex;
  align-items: center;
  padding: 8px 16px;
  transition: background-color 0.3s;
}

.submenu-item:hover {
  background-color: #f9f9f9;
}

.submenu-item-text {
  font-size: 14px;
  color: #555;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: flex-end; /* Align content to the right */
  margin-left: auto; /* Push the content to the right */
}

.footer-section {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.footer-title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 8px;
  color: #ffffff;
}

.footer-item {
  display: flex;
  align-items: center;
  margin-bottom: 4px;
  color: #ffffff;
}

.footer-icon {
  margin-right: 8px;
  color: #ffd700; /* Gold color for icons */
}

.backgroundfooter {
  background-color: #191970;
}
.begrounfoter {
  background-color: #191970;
}
</style>
