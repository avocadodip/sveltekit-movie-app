<script context="module">
  export async function load({ fetch, params }) {
    const url = 
      `https://api.themoviedb.org/3/search/movie?api_key=56d7cc636840c4b7265c305a22ba1519&language=en-US&query=${params.id}&page=1&include_adult=false`
    const res = await fetch(url);
    const data = await res.json();
    if (res.ok) {
      return {
        props: { searchedMovies: data.results }
      }
    }
  }

</script>

<script>
  import Card from '../../components/Card.svelte';
  export let searchedMovies;
</script>

<div class="grid grid-cols-3 gap-x-8 gap-y-12 mt-3">
  {#each searchedMovies as movie}
    <Card {movie}/>
  {/each}
</div>