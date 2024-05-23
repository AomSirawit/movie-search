<template>
  <div
    class="flex flex-col justify-center align-middle h-96 bg-slate-800 text-center" id="search">
    <h1 class="text-white text-3xl font-bold mb-5">Search Your Movie</h1>
    <div>
      <input
        v-model="searchQuery"
        class="input input-bordered w-full max-w-xs"
        type="text"
        placeholder="🔍 Quick Search"
      />
      <div class="card-actions flex justify-center">
        <button @click="searchMovie" class="btn btn-primary text-white mt-3">
          Search
        </button>
      </div>
      <p v-if="errorMessage" class="text-red-500">{{ errorMessage }}</p>
    </div>
    <div
      v-if="showModal"
      class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50 text-cent"
    >
      <div class="bg-white p-8 rounded-lg shadow-lg max-w-lg w-full">
        <h2 class="text-2xl font-bold mb-4 text-center">
          {{ movie.Title }} {{ movie.Year }}
        </h2>
        <div class="flex justify-center">
          <img
            :src="movie.Poster"
            alt="Movie Poster"
            class="mb-4"
            v-if="movie.Poster !== 'N/A'"
          />
        </div>
        <div class="ml-4">
          <p><strong>Director</strong> : {{ movie.Director }}</p>
          <p><strong>Genre</strong> : {{ movie.Genre }}</p>
          <p><strong>Plot</strong> : {{ movie.Plot }}</p>
          <p><strong>Rating</strong> : {{ movie.imdbRating }} <i class="fa-solid fa-star" style="color: #FFD43B;"></i></p>
        </div>
        <div class="flex justify-center">
          <button
            @click="closeModal"
            class="btn btn-error text-white mt-3 w-52"
          >
            <i class="fa-solid fa-x" style="color: #ffffff"></i>
          </button>
        </div>
      </div>
    </div>
    <div
      v-if="loading"
      class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50 text-white"
    >
      <span class="loading loading-spinner loading-lg"></span>
    </div>
  </div>
</template>
  
  <script>
import axios from "axios";
export default {
  name: "SearchSection",
  data() {
    return {
      searchQuery: "",
      movie: null,
      errorMessage: "",
      showModal: false,
      loading: false,
    };
  },
  methods: {
    searchMovie() {
      if (this.searchQuery) {
        this.loading = true;
        axios
          .get(`https://www.omdbapi.com/?t=${this.searchQuery}&apikey=df9bdcb2`)
          .then((response) => {
            if (response.data.Response === "True") {
              this.movie = response.data;
              this.errorMessage = "";
              this.showModal = true;
            } else {
              this.movie = null;
              this.errorMessage = response.data.Error;
              this.showModal = false;
            }
          })
          .catch((error) => {
            console.error("Fetching the movie failed!", error);
            this.errorMessage = "Fetching the movie failed!";
            this.movie = null;
            this.showModal = false;
          })
          .finally(() => {
            this.loading = false;
          });
      } else {
        this.errorMessage = "Please enter a movie title";
        this.movie = null;
        this.showModal = false;
      }
    },
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>
  
  <style scoped>
</style>