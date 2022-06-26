<script context="module">
  export async function load({fetch}) {
    const res  = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${import.meta.env.VITE_API_KEY}&language=en-US&page=1`);
    const data = await res.json();
    if(res.ok){
      return {
        props: {
          popular: data.results
        }
      };
    }
  }

</script>

<script>
import.meta.env.VITE_API_KEY

  import PopularMovies from "../components/popular-movies.svelte";
  export let popular;
import Search from "../components/search-movies.svelte";
import {fly } from "svelte/transition";

</script>

<section in:fly={{
  y: 50, duration: 500
   }}
   out:fly={{
    duration: 500,
    delay: 500
   }}>
  <Search/> 
  <PopularMovies {popular} />
</section>