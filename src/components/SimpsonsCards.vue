<script setup>
import axios from 'axios';
import { ref } from 'vue';
import Card from './Card.vue';

const episodes = ref([]);

const fetchEpisodes = async () => {
  try {
    const response = await axios.get('https://api.sampleapis.com/simpsons/episodes');

    episodes.value = response.data;
  } catch (error) {
    console.error('Error fetching episodes:', error);
  }
};

fetchEpisodes();
</script>

<template>
  <div class="container">
    <div class="cards">
      <Card
        v-for="episode in episodes"
        :key="episode.id"
        :image="episode.thumbnailUrl"
        :name="episode.name"
      >
        <div class="episode-details">
          <p><strong>Season:</strong> {{ episode.season }}</p>
          <p><strong>Episode:</strong> {{ episode.episode }}</p>
          <p><strong>Rating:</strong> {{ episode.rating }}</p>
          <p><strong>Air Date:</strong> {{ new Date(episode.airDate).toLocaleDateString() }}</p>
          <p><strong>Description:</strong> {{ episode.description }}</p>
        </div>
      </Card>
    </div>
  </div>
</template>

<style scoped>
.container {
  background-color: rgb(27, 26, 26);
  padding: 30px;
}
.cards {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}
.cards h3 {
  font-weight: bold;
}
.cards p {
  font-size: 10px;
}

.button-container {
  display: flex;
  justify-content: center;
  padding-top: 30px;
}
.button-container button {
  border: none;
  width: 50px;
  height: 50px;
  border-radius: 100%;
  margin: 0 5px;
  cursor: pointer;
}
.spinner {
  display: flex;
  align-items: center;
  justify-content: center;
}

p {
  font-size: 10px;
}

.jobs {
  display: flex;
  flex-wrap: wrap;
}
</style>
