<script context="module">
  //https://www.youtube.com/watch?v=ydR_M0fw9Xc&ab_channel=DevEd
  // 1:12:31
  export async function load({ fetch }) {
    const url = 
      `https://api.themoviedb.org/3/movie/popular?api_key=${process.env.API_URL}`;
    const res = await fetch(url);
    const data = await res.json();
    if (res.ok) {
      return {
        props: { movies: data.results }
      }
    }

  }
</script>

<svelte:head>
  <title>Chris Movies</title>
</svelte:head>

<script>
  import Card from '../components/Card.svelte';
  import Search from '../components/Search.svelte';
  import { fly } from 'svelte/transition';
  export let movies;

  // idea! add filter by genre

</script>

<div in:fly={{ y: 50, duration: 500 }} out:fly={{ duration: 500 }} class="flex flex-col items-center py-6 space-y-8">
  <h1 class="text-4xl">Chris' Movie Database</h1>
  <Search />
</div>


<div in:fly={{ y: 50, duration: 500 }} out:fly={{ duration: 500 }} class="grid grid-cols-3 gap-x-8 gap-y-12 mt-3">
  {#each movies as movie}
    <Card {movie}/>
  {/each}
</div>

