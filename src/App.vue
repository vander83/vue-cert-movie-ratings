<script setup>
import { ref } from "vue";
import { items } from "./movies.json";
/*
 This is an Icon that you can use to represent the stars if you like
 otherwise you could just use a simple ⭐️ emoji, or * character.
*/
import { StarIcon } from "@heroicons/vue/24/solid";

const movies = ref(items);

</script>

<template>
  <!-- This is where your template goes	-->
  <div>
    <main class="movies-container">
      <div class="movies">
        <div class="movie" v-for="movie in items" :key="movie.id">
          <div class="image-section">
            <img :src="movie.image" alt="">
          </div>
          <div class="text-section">
            <h3 class="movie-name">{{ movie.name }}</h3>
            <div class="movie-genre-list">
              <div class="movie-genre" v-for="genre in movie.genres" :key="`${movie.id}-${genre}`">
               <span>{{ genre }}</span>
              </div>
            </div>
            <div class="movie-description">{{ movie.description }}</div>
            <div class="movie-rating">
              <span>Rating ({{ movie.rating }}/5)</span>
              <div class="stars">
                <StarIcon class="star" v-for="star in movie.rating" :key="`star-${star}`"/>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped>
.movies-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  background-color: #121826;
  padding: 2rem;
}
.movies {
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}
.movie {
  width: 300px;
  height: max-content;
}

.image-section {
  width: 100%;
  height: 420px;
}

.image-section img {
  width: 100%;
  max-height: 100%;
  object-fit: cover;
  border-radius: 10px 10px 0 0;
}

.text-section {
  height: max-content;
  padding: 1rem;
  border-radius: 0 0 10px 10px;
  background-color: #fff;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto auto 100px auto;
}

.movie-name {
  font-size: 1.2rem;
  font-weight: bold;
}

.movie-genre-list {
  display: flex;
  flex-direction: row;
  gap: 0.5rem;
}

.movie-genre {
  background-color: #6466f0;
  padding: 2px 8px;
  border-radius: 20px;
  color: #fff;
  font-size: 0.75rem;
}

.movie-description {
  font-size: 0.75rem;
  margin-top: 0.5rem;
  overflow: hidden;
}

.movie-rating {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 0.5rem;
  margin-top: 0.5rem;
}

.stars {
  display: flex;
  flex-direction: row;
  gap: 0.25rem;
}

.star {
  color: #fbbf24;
  width: 1rem;
  height: 1rem;
}
</style>
