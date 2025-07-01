<template>
  <div>
    <p v-if="user">
      Нэвтэрсэн: {{ user.email }}
      | <button @click="logout">Гарах</button>
    </p>
    <p v-else>
      <router-link to="/login">Нэвтрэх</router-link>
    </p>

    <router-view />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const user = ref(null);

onMounted(() => {
  const u = localStorage.getItem('user');
  if (u) user.value = JSON.parse(u);
});

const logout = () => {
  localStorage.removeItem('user');
  user.value = null;
  router.push('/login');
};
</script>

<style>
body {
  font-family: sans-serif;
}
</style>
