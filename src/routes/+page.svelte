<script lang="ts">
	import '@fontsource-variable/bricolage-grotesque';
	import '../app.css';

	import Navbar from '$lib/components/Navbar.svelte';
	import Home from '$lib/components/Home.svelte';
	import Features from '$lib/components/Features.svelte';
	import Showcase from '$lib/components/Showcase.svelte';
</script>

<Navbar />

<main>
	<Home />
	<Features />
	<Showcase />
</main>

<footer class="py-10 text-xs text-center text-zinc-500">2024 ©️ Pixzip</footer>
