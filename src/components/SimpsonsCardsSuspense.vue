<script setup>
import SimpsonsCards from './SimpsonsCards.vue';
</script>

<template>
  <Suspense>
    <template #default>
      <SimpsonsCards />
    </template>
    <template #fallback>
      <div class="cards">
        <NSpin size="large" />
      </div>
    </template>
  </Suspense>
</template>

<style scoped>
.cards {
  background-color: rgb(27, 26, 26);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
