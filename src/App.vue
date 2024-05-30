<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-purple text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title class="q-ml-md">
          <q-avatar size="42px">
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          <span class="q-ml-sm text-h6">Toko Lightstick K-Pop</span>
        </q-toolbar-title>
      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab to="/home" label="Beranda" />
        <q-route-tab to="/top-seller" label="Top Seller" />
        <q-route-tab to="/about" label="Tentang Kami" @click.prevent="openDrawer" />
      </q-tabs>
    </q-header>

    <!-- Drawer -->
    <q-drawer v-model="leftDrawerOpen" side="left" bordered>
      <q-scroll-area class="fit">
        <q-list padding class="menu-list">
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="inbox" />
            </q-item-section>
            <q-item-section class="text-black"> Inbox </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="star" />
            </q-item-section>
            <q-item-section class="text-black"> Star </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="send" />
            </q-item-section>
            <q-item-section class="text-black"> Send </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="drafts" />
            </q-item-section>
            <q-item-section class="text-black"> Drafts </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <!-- Page Container -->
    <q-page-container>
      <q-page class="q-pa-md">
        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          animated
          infinite
          control-color="white"
          arrows
          navigation
          navigation-position="bottom"
          swipeable
          transition-prev="slide-right"
          transition-next="slide-left"
        >
          <q-carousel-slide
            name="1"
            img-src="https://sweezy-cursors.com/wp-content/uploads/cursor/bts-lightstick/bts-lightstick-custom-cursor.png"
          >
            <div class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm">
              Lightstick Terbaik!
            </div>
          </q-carousel-slide>
          <q-carousel-slide
            name="2"
            img-src="https://cdn.custom-cursor.com/packs/2870/k-pop-blackpink-lightstick-pack.png"
          >
            <div class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm">
              Diskon Spesial!
            </div>
          </q-carousel-slide>
          <q-carousel-slide
            name="3"
            img-src="https://i.pinimg.com/736x/c0/bb/83/c0bb83bba761685645cbee0fcfac703b.jpg"
          >
            <div class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm">
              Lightstick Terbaru!
            </div>
          </q-carousel-slide>
        </q-carousel>

        <!-- Card Section -->
        <div class="row q-col-gutter-md q-pt-md">
          <q-card
            v-for="(lightstick, index) in lightsticks"
            :key="index"
            class="col-xs-12 col-sm-6 col-md-4 q-hover-shadow"
          >
            <q-img :src="lightstick.image" class="q-mb-sm image-hover" style="max-height: 300px;" />
            <q-card-section>
              <div class="text-subtitle1 text-black">{{ lightstick.name }}</div>
              <div class="text-caption text-black">{{ lightstick.description }}</div>
              <div class="text-h6 text-primary">{{ lightstick.price }}</div>
              <q-rating :value="lightstick.rating" max="5" size="16px" readonly />
            </q-card-section>
            <q-card-actions align="right">
              <q-btn flat label="Detail" color="purple" />
              <q-btn flat label="Add to Cart" color="purple" />
              <q-btn flat label="Delete" color="red" @click="deleteLightstick(index)" />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-purple text-white q-pa-md">
      <div class="row items-center">
        <div style="text-align: center;" class="col text-white">© 2024 Toko Lightstick K-Pop</div>
        <div class="col-auto">
          <q-btn flat round icon="fab fa-facebook" class="text-white q-mr-sm" />
          <q-btn flat round icon="fab fa-twitter" class="text-white q-mr-sm" />
          <q-btn flat round icon="fab fa-instagram" class="text-white" />
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref("1");
    const lightsticks = ref([
      {
        name: "BTS Lightstick",
        description: "Lightstick resmi BTS",
        image: "https://www.kpop.ae/cdn/shop/products/BTSlightstickmapofthesoul.png?v=1677135649",
        price: "Rp 1.118.000",
        rating: 5,
      },
      {
        name: "TXT Lightstick",
        description: "Lightstick resmi TXT",
        image: "https://kplaceshop.com/cdn/shop/files/txt-official-lightstick-ver-2-main-image_1200x.png?v=1715849582",
        price: "Rp 1.126.000",
        rating: 5,
      },
      {
        name: "GOT7 Lightstick",
        description: "Lightstick resmi GOT7",
        image: "https://www.delivered.co.kr/wp-content/uploads/2021/08/GOT7-LIGHTSTICK-VERSION-2.jpeg",
        price: "Rp 550.000",
        rating: 3,
      },
      {
        name: "Enhypen Lightstick",
        description: "Lightstick resmi Enhypen",
        image: "https://img.ws.mms.shopee.co.id/0bfe00b96aa2ee3387ce790deb059b02",
        price: "Rp 4.055.000",
        rating: 4,
      },
      {
        name: "Seventeen Lightstick",
        description: "Lightstick resmi Seventeen",
        image: "https://www.amuseground.com/cdn/shop/files/60df2905ae77748c9897599b89651050.png?v=1701052439",
        price: "Rp 1.437.040",
        rating: 2,
      },
      {
        name: "MAMAMOO Lightstick",
        description: "Lightstick resmi MAMAMOO",
        image: "https://ae01.alicdn.com/kf/S4f5627d48ecc482480511c36320e0087w/Kpop-MAMAMOO-Lightstick-konser-cahaya-lampu-terang-bersorak-tongkat-cahaya-koleksi-mainan-penggemar.jpg",
        price: "Rp 800.000",
        rating: 5,
      },
      {
        name: "Blackpink Lightstick",
        description: "Lightstick resmi Blackpink",
        image: "https://image.popmama.com/content-images/post/20230308/cara-membedakan-lightstick-blackpink-asli-dan-palsu-25b3535726474dee291f7f69e01098b6.jpg?width=800&height=420",
        price: "Rp 1.133.000",
        rating: 4,
      },
      {
        name: "Twice Lightstick",
        description: "Lightstick resmi Twice",
        image: "https://images-cdn.ubuy.qa/6352a2c9a6f1fe2eed34f574-twice-official-light-stick-candy-bong.jpg",
        price: "Rp 795.000",
        rating: 3,
      },
      {
        name: "Treasure Lightstick",
        description: "Lightstick Treasure ",
        image: "https://ae01.alicdn.com/kf/S2a7d7ef0802745008422ec03baee7cf1G.jpg_640x640Q90.jpg_.webp",
        price: "Rp 1.161.000",
        rating: 5,
      },
    ]);

    function toggleLeftDrawer() {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    }

    function openDrawer() {
      leftDrawerOpen.value = true;
    }

    function deleteLightstick(index) {
      lightsticks.value.splice(index, 1);
    }

    return {
      leftDrawerOpen,
      slide,
      lightsticks,
      toggleLeftDrawer,
      openDrawer,
      deleteLightstick,
    };
  },
};
</script>

<style>
.menu-list {
  padding-top: 20px;
}

.q-hover-shadow:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.q-carousel-slide .absolute-bottom {
  background: rgba(0, 0, 0, 0.5);
  padding: 1rem;
  text-align: center;
  width: 100%;
}

.image-hover {
  transition: transform 0.3s ease;
}

.image-hover:hover {
  transform: scale(1.1);
}

.text-black {
  color: black;
}

.q-footer {
  background-color: #6a1b9a !important;
  color: white !important;
}
</style>
