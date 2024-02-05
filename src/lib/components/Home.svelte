<script lang="ts">
	import { onMount } from 'svelte';

	let version = '';
	let date = '';

	onMount(() => {
		fetch('https://api.github.com/repos/richhost/pixzip/releases/latest').then((resp) => {
			resp.json().then((data) => {
				version = data.tag_name.replace('v', '');
				date = new Date(data.published_at).toLocaleDateString('en-US', {
					year: 'numeric',
					month: '2-digit',
					day: '2-digit'
				});
			});
		});
	});
</script>

<section id="home" class="px-5 font-semibold py-10">
	<div class="max-w-4xl mx-auto py-6">
		<img src="/1.webp" alt="screenshot" class="aspect-[2000/1481]" />
	</div>

	<div class="text-center text-primary mb-2">Save your storage now</div>
	<h1 class="mx-auto text-[clamp(32px,4vw,48px)] text-center leading-10">
		Compress images quickly & free!
	</h1>

	<div class="flex mt-10 items-center justify-center gap-5">
		<a
			href="https://github.com/richhost/pixzip/releases"
			target="_blank"
			class="rounded-full py-2 px-4 hover:shadow-lg bg-primary text-white active:bg-muted transition-all"
			>Free Download</a
		>
		<a
			href="https://www.123pan.com/s/072SVv-0Eecv.html"
			target="_blank"
			rel="noreferrer"
			class="hover:drop-shadow-lg transition-all text-primary active:text-muted font-normal text-sm hidden md:block"
		>
			Download for China
		</a>
	</div>
	<p class="mt-5 text-xs font-normal text-zinc-500 text-center">Supports macOS & Windows</p>
	<p class="text-xs font-normal text-zinc-500 text-center">
		Version: {version}, Updated: {date}
	</p>
</section>
