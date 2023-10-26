<script setup>
const props = defineProps({
  product: {
    type: Object,
    default: {},
  },
});

// Kategori produk yang dipilih
let selectedCategory = "Semua Kategori";

// Data kategori produk
const categories = ["Semua Kategori", "Baju", "Sepatu", "Celana"]; // Sesuaikan dengan kategori yang ada

// Fungsi untuk memfilter produk berdasarkan kategori
const filterByCategory = () => {
  // Di sini, Anda dapat mengirimkan kategori yang dipilih ke komponen induk atau komponen lain untuk melakukan filter.
  // Misalnya, Anda dapat mengirimkan peristiwa (event) bahwa produk perlu difilter dengan kategori yang dipilih.
};
</script>

<template>
  <section class="bg-white shadow-xl rounded-xl overflow-hidden">
    <div :class="`w-full h-[200px] p-5 bg-gray-300`">
      <img :src="props.product.image" class="w-full h-full object-contain" />
    </div>
    <div class="px-5 pb-5 pt-9 relative">
      <NuxtLink :to="`/product/${props.product.id}`"
        ><h3 class="text-lg font-bold mb-4 text-limit limit-2">
          {{ props.product.name }}
        </h3></NuxtLink
      >

      <!-- Tambah elemen UI untuk memilih kategori -->
      <div class="mb-2">
        <select v-model="selectedCategory" @change="filterByCategory">
          <option
            v-for="category in categories"
            :key="category"
            :value="category"
          >
            {{ category }}
          </option>
        </select>
      </div>

      <div class="flex justify-between items-center">
        <span class="text-sm font-normal">{{ props.product.category }}</span>
        <span class="text-sm font-normal">${{ props.product.price }}</span>
      </div>

      <div
        :class="`cursor-pointer absolute -top-5 right-7 w-[50px] h-[50px] bg-
      white shadow-xl rounded-full flex justify-center items-center hover:bg-blue-600

    hover:text-white transition duration-300`"
      >
        <i class="ri-shopping-cart-2-line"></i>
      </div>
    </div>
  </section>
</template>
