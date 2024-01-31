<script lang="ts">
	const contents = [
		{
			title: '🚀 Workspace',
			description:
				'You can combine any configuration of output size, output format, compression strength, etc., and switch them freely.'
		},
		{
			title: '🌈 Popular format',
			description: 'Batch compress JPG/PNG/GIF/WebP/AVIF.'
		},
		{
			title: '📥 Local compression',
			description:
				"No data will be uploaded, so you don't have to worry about your photos being leaked."
		},
		{
			title: '❤️ Free software',
			description:
				'All people and businesses can use this software for free, and the source code is open.'
		}
	];
</script>

<section
	id="features"
	class="px-5 max-w-7xl mx-auto mt-20 grid gap-10 grid-cols-1 md:grid-cols-2 xl:grid-cols-4"
>
	{#each contents as item}
		<article>
			<h3 class="text-xl font-medium">{item.title}</h3>
			<p class="text-zinc-600">
				{item.description}
			</p>
		</article>
	{/each}
</section>
