<template>
    <div class="flex items-center justify-center min-h-screen bg-slate-800 py-10" id="faq">
      <div class="w-full max-w-md">
        <h1 class="font-semibold text-3xl text-center text-white mb-10">FAQ</h1>
        <div class="flex flex-col items-center space-y-6 px-4 md:px-0">
          <div
            tabindex="0"
            class="collapse collapse-arrow border border-base-300 bg-base-200 w-full rounded-lg shadow-lg"
          >
            <div class="collapse-title text-lg font-medium">
              What movies can I search for?
            </div>
            <div class="collapse-content">
              <p>
                This website uses the OMDb API to search for movies. While the
                database is vast, it may not include every single movie ever made.
                However, it covers a large range of films, including recent
                releases, classics, and independent productions.
              </p>
            </div>
          </div>
    
          <div
            tabindex="1"
            class="collapse collapse-arrow border border-base-300 bg-base-200 w-full rounded-lg shadow-lg"
          >
            <div class="collapse-title text-lg font-medium">
              How do I search for a specific movie?
            </div>
            <div class="collapse-content">
              <p>
                Simply enter the title of the movie you're looking for in the search
                bar provided on the homepage.
              </p>
            </div>
          </div>
    
          <div
            tabindex="2"
            class="collapse collapse-arrow border border-base-300 bg-base-200 w-full rounded-lg shadow-lg"
          >
            <div class="collapse-title text-lg font-medium">
              What information will I see about each movie?
            </div>
            <div class="collapse-content">
              <p>- Title</p>
              <p>- Year</p>
              <p>- Director</p>
              <p>- Genre</p>
              <p>- Plot</p>
              <p>- Rating</p>
            </div>
          </div>
    
          <div
            tabindex="3"
            class="collapse collapse-arrow border border-base-300 bg-base-200 w-full rounded-lg shadow-lg"
          >
            <div class="collapse-title text-lg font-medium">
              Why can't I find a movie I'm looking for?
            </div>
            <div class="collapse-content">
              <p>- The movie may not be included in the OMDb database.</p>
              <p>- There may be typos in your search query.</p>
              <p>- The movie's title may be very obscure or not well-known.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "FaqSection",
  };
  </script>
  
  <style>
  /* Optional custom styles if needed */
  </style>
  