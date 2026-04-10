<!-- Login.vue -->
<template>
  <div class="auth-form">
    <h2>Вход</h2>
    <form @submit.prevent="handleAuth('/auth/login')">
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="password" type="password" placeholder="Пароль" required />
      <button :disabled="loading">{{ loading ? 'Вход...' : 'Войти' }}</button>
      <p v-if="error" class="error">{{ error }}</p>
    </form>
    <p>Нет аккаунта? <router-link to="/auth/register">Зарегистрироваться</router-link></p>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { apiFetch } from '../api';

const email = ref(''); const password = ref('');
const loading = ref(false); const error = ref('');
const router = useRouter();

async function handleAuth(endpoint) {
  loading.value = true; error.value = '';
  try {
    const res = await apiFetch(endpoint, {
      method: 'POST',
      body: JSON.stringify({ email: email.value, password: password.value })
    });
    localStorage.setItem('token', res.token);
    localStorage.setItem('user', JSON.stringify(res.user));
    router.push('/profile');
  } catch (e) { error.value = e.message; }
  finally { loading.value = false; }
}
</script>