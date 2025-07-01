<template>
  <div class="card">
    <h2>{{ recipe.title }}</h2>
    <img :src="recipe.image" alt="Жор зураг" />
    <p>{{ recipe.ingredients.join(', ') }}</p>
    <button @click="$emit('save', recipe)">Жор хадгалах</button>
  </div>
</template>

<script setup>
defineProps(['recipe']);
</script>

<style>
.card {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}
</style>
