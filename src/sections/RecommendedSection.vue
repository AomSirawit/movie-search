<template>
    <div class="h-fit m-10" id="recommended">
      <h1 class="font-semibold text-3xl text-center">Recommended Movies</h1>
      <div
        v-if="loading"
        class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50 text-white"
      >
        <span class="loading loading-spinner loading-lg"></span>
      </div>
      <div v-else class="flex flex-wrap justify-center">
        <div
          v-for="(movie, index) in movies"
          :key="index"
          class="w-96 bg-base-100 shadow-xl m-4"
        >
          <figure class="px-10 pt-10">
            <img
              v-if="movie.Poster"
              :src="movie.Poster"
              :alt="movie.Title"
              class="rounded-xl"
            />
          </figure>
          <div class="card-body items-center text-center">
            <h2 class="card-title">{{ movie.Title }}</h2>
            <p>{{ movie.Plot }}</p>
            <p>{{ movie.imdbRating }} <i class="fa-solid fa-star" style="color: #FFD43B;"></i> </p>
          
          </div>
        </div>
      </div>
    </div>
  </template>
    
    <script>
  import axios from "axios";
  
  export default {
    name: "RecommendedSection",
    data() {
      return {
        loading: true,
        movies: [],
      };
    },
    methods: {
      async fetchMovies() {
        try {
          this.loading = true;
  
          const response = await axios.get("http://www.omdbapi.com/", {
            params: {
              apikey: "df9bdcb2",
              s: "Marvel",
              type: "movie",
            },
          });
          const movies = response.data.Search;
  
          // Sort movies by ratings
          movies.sort(
            (a, b) => parseFloat(b.imdbRating) - parseFloat(a.imdbRating)
          );
  
          // Take top 3 movies
          const topThreeMovies = movies.slice(0, 3);
  
          const detailsPromises = topThreeMovies.map((movie) => {
            return axios.get("http://www.omdbapi.com/", {
              params: {
                apikey: "df9bdcb2",
                i: movie.imdbID,
              },
            });
          });
  
          const detailsResponses = await Promise.all(detailsPromises);
          this.movies = detailsResponses.map((response) => response.data);
        } catch (error) {
          console.error("Error fetching movie data:", error);
        } finally {
          this.loading = false;
        }
      },
    },
    mounted() {
      this.fetchMovies();
    },
  };
  </script>
    
    <style>
  </style>
    