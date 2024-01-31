<script lang="ts">
	let container: HTMLElement;

	let percentage = 40;
	let active = false;

	const onpointerdown = (event: PointerEvent) => {
		event.preventDefault();
		active = true;
		const target = event.target as HTMLElement;
		target.setPointerCapture(event.pointerId);
	};

	const onpointermove = (event: PointerEvent) => {
		if (!active) return;
		let left = event.clientX - container.getBoundingClientRect().left;
		if (left < 0) left = 0;
		let rightEdge = container.offsetWidth;
		if (left > rightEdge) left = rightEdge;
		percentage = (left / container.offsetWidth) * 100;
	};

	const onpointerup = (event: PointerEvent) => {
		const target = event.target as HTMLElement;
		if (target.hasPointerCapture(event.pointerId)) {
			target.releasePointerCapture(event.pointerId);
		}
		active = false;
	};
</script>

<div
	class="relative cursor-col-resize overflow-hidden inline-block touch-none"
	on:pointerdown={onpointerdown}
	on:pointermove={onpointermove}
	on:pointerup={onpointerup}
	bind:this={container}
>
	<img
		src="https://picsum.photos/400/200"
		alt=""
		draggable="false"
		style="clip-path: polygon(0 0, {percentage}% 0, {percentage}% 100%, 0 100%);"
	/>
	<img
		src="https://picsum.photos/id/404/400/200"
		class="absolute top-0"
		alt=""
		draggable="false"
		style="clip-path: polygon({percentage}% 0, 100% 0, 100% 100%, {percentage}% 100%);"
	/>
	<div
		class="absolute inset-y-0 flex flex-col items-center w-10 -translate-x-1/2"
		style="left: {percentage}%;"
	>
		<div class="grow w-0.5 bg-white shadow" />
		<div
			class="w-10 h-10 border-2 rounded-full shadow bg-black/50 backdrop-blur flex items-center justify-center"
		>
			<div
				class="w-0 h-0"
				style="border: inset 6px transparent; border-right: 6px solid white; margin-right: 10px;"
			/>
			<div class="w-0 h-0" style="border: inset 6px transparent; border-left: 6px solid white;" />
		</div>
		<div class="grow w-0.5 bg-white shadow" />
	</div>
</div>
