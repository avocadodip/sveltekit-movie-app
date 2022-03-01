<script>
  export let movie;
</script>

<div class="flex flex-col">
  <a href={`/movies/${movie.id}`}>
    <img src="
    {`https://www.themoviedb.org/t/p/w1280/${movie.poster_path}`}
    " 
    alt=""
    class="rounded-lg">
  </a>
  <h2 class="text-center pt-3">
    {movie.original_title}
  </h2>
</div>