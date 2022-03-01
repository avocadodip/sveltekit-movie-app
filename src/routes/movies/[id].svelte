<script context="module">
  export async function load({ fetch, params }) {
    const url = 
      `https://api.themoviedb.org/3/movie/${params.id}?api_key=56d7cc636840c4b7265c305a22ba1519`;
    const res = await fetch(url);
    const movieDetails = await res.json();
    if (res.ok) {
      return {
        props: { movieDetails }
      }
    }
  }
</script>

<script>
  export let movieDetails;

</script>

<svelte:head>
  <title>{movieDetails.original_title}</title>
</svelte:head>

<img src="{`https://www.themoviedb.org/t/p/w1280/${movieDetails.backdrop_path}`}" alt="" class="rounded-lg">
<h1 class="font-bold text-2xl py-4">{movieDetails.original_title}</h1>
<p>{movieDetails.overview}</p>
<div class="pt-7">
  <p>Release Date: {movieDetails.release_date}</p>
  <p>Runtime: {movieDetails.runtime} minutes</p>
</div>
