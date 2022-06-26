<script>
  export let popular;
import MovieCard from "./movie-card.svelte"
</script>


<h3>Popular Movie</h3>
<div class="popular-movies">
{#each popular as movie}
  <div class="movie">
    <!-- <img src="https://image.tmdb.org/t/p/w500/{movie.poster_path}" alt="{movie.title}" /> -->
    <MovieCard movie={movie} />
  </div>
{/each}
</div>

<style>
  h3 {
    padding: 0 1rem;
  }

  .popular-movies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
grid-column-gap: 1rem;
grid-row-gap: 2rem;

  }
  </style>