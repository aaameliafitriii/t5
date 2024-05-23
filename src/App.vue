<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="./assets/Screenshot (672).png" alt="Logo Toko Online" />
          </q-avatar>
          Toko Online
        </q-toolbar-title>
        <!-- Tambahkan tombol pencarian di sini -->
        <q-space />
        <q-input
          filled
          dense
          placeholder="Cari produk..."
          prepend-icon="search"
          class="bg-white q-ma-none"
        >
          <template v-slot:append>
            <q-icon name="shopping_cart" />
          </template>
        </q-input>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <div class="q-pa-md">
        <div class="q-gutter-md">
          <q-carousel
            v-model="slide"
            transition-prev="scale"
            transition-next="scale"
            swipeable
            animated
            control-color="white"
            navigation
            padding
            arrows
            height="650px"
            class="bg-primary text-white shadow-1 rounded-borders"
          >
            <q-carousel-slide
              v-for="(item, index) in slides"
              :key="index"
              :name="'slide' + index"
              class="column no-wrap flex-center"
            >
              <q-img
                :src="item.image"
                :alt="'Slide ' + (index + 1)"
                style="width: 100%; height: 100%; object-fit: cover !important"
              />
              <div class="q-mt-md text-center">
                {{ item.text }}
              </div>
              <!-- Tombol BUY NOW! -->
              <q-btn color="yellow" class="q-mt-md" label="BUY NOW!" />
            </q-carousel-slide>
          </q-carousel>
        </div>
      </div>

      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card">
          <img src="https://esports.id/img/article/434120210202044608.jpg" />

          <q-card-section>
            <div class="text-h6">Toko Gaming Elektronik</div>
            <div class="text-subtitle2">by amelia fitri</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            {{ lorem }}
          </q-card-section>
        </q-card>
      </div>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <div>&copy; 2024 Amelia fitri. All rights reserved.</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  setup() {
    const slide = ref(0);
    const slides = ref([
      {
        image:
          "https://id-media.apjonlinecdn.com/magefan_blog/1000x450px_Are_Mechanical_Keyboards_Better_Gaming.jpg",
        text: "mechanical keyboard",
      },
      {
        image:
          "https://cdn.idntimes.com/content-images/community/2022/08/basilisk-ultimate-usp5-mobile-a338ebee7963a0de04272cb76e2b071d-312085b5dbf6692121d41f4e2f86f92e.jpg",
        text: "Mouse Gaming",
      },
      {
        image:
          "https://d1tgyzt3mf06m9.cloudfront.net/v3-staging/2024/02/Rekomendasi-headset-gaming-Rexus-Headset-Gaming-Vonix-F30.-via-Istimewa.jpg",
        text: "Headset Gaming",
      },
      {
        image:
          "https://image.made-in-china.com/2f0j00ZvIlDtjHAPcO/Best-Quality-Super-Bass-Portable-Speaker-Bluetooth-Speakers-RGB-Soundbar-2-1-Gaming-Speaker.webp",
        text: "Speaker",
      },
    ]);
    const lorem =
      "Toko gaming elektronik Gaming by amelia menyediakan berbagai perangkat dan aksesori gaming berkualitas tinggi dari merek terkemuka. Lebih berfokus pada pengalaman berbelanja yang responsif dan ramah pengguna, dengan penekanan pada kualitas produk, dan layanan pelanggan yang baik.";
    onMounted(() => {
      setTimeout(() => {
        slide.value = 0;
      }, 100);
    });
    return {
      slide,
      slides,
      lorem,
    };
  },
};
</script>

<style>
.bg-grey-8 {
  text-align: center;
}
.bg-white {
  background-color: white;
}
.my-card {
  width: 100%;
  max-width: 250px;
}
</style>