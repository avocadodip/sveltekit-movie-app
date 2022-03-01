<script>
  import {goto} from '$app/navigation';

  let value = '';

  let isEmpty = true;
	$: if (value != '') {
		isEmpty = false;
	}
	else {
		isEmpty = true;
	}

  const search = () => {
    goto(`/search/${value}`);
  }
</script>

<form class="flex" on:submit|preventDefault={search}>
  <input 
    bind:value={value} 
    class="focus:outline-none bg-slate-600 text-white rounded-l-xl pl-4" 
    type="text" 
    placeholder="Search Movie..."
  >

  <button 

    class="shadow appearance-none rounded-r-xl w-full py-2 px-3 text-gray-700 bg-green-500 leading-tight focus:outline-none"
    class:bg-gray-100={isEmpty}
    class:text-gray-400={isEmpty}
    disabled={isEmpty}
  >Go</button>

</form>