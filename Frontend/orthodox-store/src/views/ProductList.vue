<template>
  <div class="products">
    <h2>Каталог товаров</h2>
    <div class="filters">
      <input v-model="search" placeholder="Поиск..." @input="fetchProducts" />
      <select v-model="category" @change="fetchProducts">
        <option value="">Все категории</option>
        <option value="иконы">Иконы</option>
        <option value="книги">Книги</option>
      </select>
    </div>
    <div v-if="loading" class="loading">Загрузка...</div>
    <div v-else class="grid">
      <div v-for="p in products" :key="p.id" class="card">
        <img v-if="p.image_url" :src="p.image_url" :alt="p.name" />
        <h3>{{ p.name }}</h3>
        <p class="price">{{ p.price }} ₽</p>
        <p class="cat">{{ p.category }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { apiFetch } from '../api';

const products = ref([]); const search = ref(''); const category = ref(''); const loading = ref(true);

async function fetchProducts() {
  loading.value = true;
  try {
    const params = new URLSearchParams();
    if (search.value) params.set('search', search.value);
    if (category.value) params.set('category', category.value);
    const res = await apiFetch(`/products?${params}`);
    products.value = res.products;
  } catch (e) { console.error(e); }
  finally { loading.value = false; }
}
onMounted(fetchProducts);
</script>