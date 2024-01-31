<script lang="ts">
	import '@fontsource-variable/bricolage-grotesque';
	import '../app.css';

	import Navbar from '$lib/components/Navbar.svelte';
	import Home from '$lib/components/Home.svelte';
	import Features from '$lib/components/Features.svelte';
</script>

<Navbar />

<main>
	<Home />
	<Features />
</main>