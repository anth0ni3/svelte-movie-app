<script>
  export let movie
  </script>


<div class="movie-card">
  <a sveltekit:prefetch sveltekit:noscroll href={`/movie/` + movie.id}>
  <img src="https://image.tmdb.org/t/p/w500/{movie.poster_path}" alt="{movie.title}" /></a>
  <div class="description">
  <h2>{movie.title}</h2>
  <p>{movie.release_date}</p>
  </div>
</div>


<style>
.movie-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 1rem;
}

  .movie-card img {
    width: 100%;
    object-fit: cover;
    border-radius: 1rem;
    margin-bottom: 1rem;
  }

  .movie-card h2 {
    font-size: 0.9rem;
  }

  .movie-card .description {
height: 5vh;
  }

  .movie-card p {
    font-size: 0.7rem;
  }
</style>