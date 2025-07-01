<template>
  <div>
    <h2>Нэвтрэх</h2>
    <input v-model="email" placeholder="Имэйл" />
    <input v-model="password" type="password" placeholder="Нууц үг" />
    <button @click="login">Нэвтрэх</button>
    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { users } from '../users';

const email = ref('');
const password = ref('');
const error = ref('');
const router = useRouter();

const login = () => {
  const user = users.find(u => u.email === email.value && u.password === password.value);
  if (user) {
    localStorage.setItem('user', JSON.stringify(user));
    router.push('/');
  } else {
    error.value = 'Имэйл эсвэл нууц үг буруу байна';
  }
};
</script>
