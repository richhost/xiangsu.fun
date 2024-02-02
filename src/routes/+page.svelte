<script lang="ts">
	import { MetaTags } from 'svelte-meta-tags';
	import '@fontsource-variable/bricolage-grotesque';
	import '../app.css';

	import Navbar from '$lib/components/Navbar.svelte';
	import Home from '$lib/components/Home.svelte';
	import Features from '$lib/components/Features.svelte';
	import Showcase from '$lib/components/Showcase.svelte';
</script>

<MetaTags
	title="Pixzip - Compress images quickly & free!"
	description="Compress images quickly & free!"
	keywords={[
		'pixzip',
		'avif',
		'webp',
		'开源图片压缩软件',
		'open source image compression software',
		'图片压缩软件',
		'image compression software',
		'图片压缩',
		'image compression',
		'图片压缩工具',
		'image compression tool'
	]}
/>

<Navbar />

<main>
	<Home />
	<Features />
	<Showcase />
</main>

<footer class="py-10 text-xs text-center text-zinc-500">2024 ©️ Pixzip</footer>
