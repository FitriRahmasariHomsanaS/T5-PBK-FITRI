<script setup>
import { ref } from "vue";

const count = ref(0);
const selectedSection = ref('');

const selectSection = (section) => {
  console.log(`Bagian yang dipilih: ${section}`);
  selectedSection.value = section;
};
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">jumlah adalah {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> untuk menguji HMR
    </p>
  </div>

  <p>
    Cek
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, starter resmi Vue + Vite
  </p>
  <p>
    Instal
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a> di IDE Anda untuk pengalaman pengembangan yang lebih baik
  </p>
  <p class="read-the-docs">Klik pada logo Vite dan Vue untuk mempelajari lebih lanjut</p>

  <!-- Bagian Beranda -->
  <section id="beranda" @click="selectSection('beranda')">
    <h2>Beranda</h2>
    <p>Selamat datang di beranda kami. Di sini Anda dapat menemukan informasi terbaru tentang produk dan layanan kami.</p>
  </section>

  <!-- Bagian Top Seller -->
  <section id="top-seller" @click="selectSection('top-seller')">
    <h2>Top Seller</h2>
    <ul>
      <li>BTS Lightstick</li>
      <li>Blackpink Lightstick</li>
      <li>TXT Lightstick</li>
    </ul>
  </section>

  <!-- Bagian Tentang Kami -->
  <section id="tentang-kami" @click="selectSection('tentang-kami')">
    <h2>Tentang Kami</h2>
    <p>Kami adalah perusahaan yang berdedikasi untuk menyediakan produk dan layanan terbaik bagi pelanggan kami.</p>
  </section>

  <!-- Bagian Hasil -->
  <div class="result">
    <h3>Hasil</h3>
    <p v-if="selectedSection === 'beranda'">Anda memilih Beranda. Di sini Anda dapat menemukan informasi terbaru tentang produk dan layanan kami.</p>
    <p v-if="selectedSection === 'top-seller'">Anda memilih Top Seller. Produk terlaris kami adalah BTS Lightstick, Blackpink Lightstick, dan TXT Lightstick.</p>
    <p v-if="selectedSection === 'tentang-kami'">Anda memilih Tentang Kami. Kami adalah perusahaan yang berdedikasi untuk menyediakan produk dan layanan terbaik bagi pelanggan kami.</p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

#beranda, #top-seller, #tentang-kami {
  margin-top: 20px;
  cursor: pointer;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

#beranda:hover, #top-seller:hover, #tentang-kami:hover {
  background-color: #f0f0f0;
}

h2 {
  color: #42b983;
}

section p {
  color: #2c3e50;
}

.result {
  margin-top: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
