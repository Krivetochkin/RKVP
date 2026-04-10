<template>
  <div class="profile">
    <h2>Профиль</h2>
    <div v-if="user" class="card">
      <p><strong>Имя:</strong> {{ user.name }}</p>
      <p><strong>Email:</strong> {{ user.email }}</p>
      <p><strong>Дата регистрации:</strong> {{ new Date(user.created_at).toLocaleDateString() }}</p>
    </div>
    <p v-else>Загрузка...</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { apiFetch } from '../api';

const user = ref(null);
onMounted(async () => {
  try { const res = await apiFetch('/auth/me'); user.value = res.user; }
  catch (e) { console.error(e); }
});
</script>