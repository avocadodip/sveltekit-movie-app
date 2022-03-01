<script>
	import '../app.css';
	import Navbar from '../components/Navbar.svelte';
	import Footer from '../components/Footer.svelte';
</script>

<div class="flex flex-col h-screen justify-between">

	<Navbar />
	
	<div class="my-1 mx-20">
		<slot />
	</div>
	
	<Footer />
</div>
