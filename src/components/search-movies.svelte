<script>
  let inputValue = "";
  let active = false;
  import {goto} from "$app/navigation";
  import {fly} from "svelte/transition";

  function cancelInactive () {
    if(!inputValue) return active = false;
    return active = true;
  }

function submitSearch(){

  goto(`/search/${inputValue}`);
}

  </script>




<form class="search" on:submit|preventDefault={submitSearch}>
  {#if !active}
  <label
  in:fly={{
    y: -10,
    duration: 500
  }}
  out:fly={{
    y: -10,
    duration: 500
  }}
  for="search_movie"> Search Movie</label>
  {/if}
  <input on:focus={() => active = true} on:blur={cancelInactive} bind:value={inputValue} name="search_movie" type="text" class={active ? "selected" : undefined}/>
  {#if inputValue}
  <button
  in:fly={{
    y: 0,
    duration: 500
  }}
  out:fly={{
    y: 0,
    duration: 500
  }}
  >Search</button>
  {/if}
</form>


<style>
  .search {
    position: relative;
    width: 30%;
    margin: 1rem;
  }

  input {
    width: 100%;
    border: none;
    font-size: 1rem;
    font-family: "Poppins";
    outline: none;
    color: rgb(255,255,255);
    padding: 0.5rem 0.1rem;
    transition: background-color 0.75s ease-out;
    font-weight: bold;
    border-radius: 10px;
    padding: 1rem;
    background-color: rgb(63,63,63);
  }

  input.selected {
    background-color: rgb(50,50,50);
  }

label {
  position: absolute;
  font-size: 0.8rem;
  top: 50%;
  left: 0%;
  transform: translate(0,-50%);
  pointer-events: none;
  color: rgb(255,255,255);
  padding: 0 1rem;
}


  button {
font-size: 0.7rem;
padding: 0 1rem;
background-color: rgb(96, 110,201);
color: white;
font-weight: bold;
border: none;
position: absolute;
bottom: 50%;
right: 0;
transform: translate(0, 50%);
height: 100%;
border-top-right-radius: 10px;
border-bottom-right-radius: 10px;
cursor: pointer
  }
</style>