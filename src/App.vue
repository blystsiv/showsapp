<script setup>
import { ref } from 'vue';
import Hero from './components/Hero.vue';
import RickMortyCards from './components/RickMortyCards.vue';
import SimpsonsCards from './components/SimpsonsCardsSuspense.vue';

const isSimpsons = ref(true);
</script>

<template>
  <main>
    <Hero :isSimpsons="isSimpsons" @selectShow="isSimpsons = !isSimpsons" />
    <KeepAlive>
      <Component :is="isSimpsons ? SimpsonsCards : RickMortyCards" />
    </KeepAlive>
  </main>
</template>
