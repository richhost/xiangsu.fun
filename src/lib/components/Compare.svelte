<script lang="ts">
	let container: HTMLElement;

	let percentage = 40;
	let active = false;

	const handleMove = (event: PointerEvent) => {
		let left = event.clientX - container.getBoundingClientRect().left;
		if (left < 0) left = 0;
		let rightEdge = container.offsetWidth;
		if (left > rightEdge) left = rightEdge;
		percentage = (left / container.offsetWidth) * 100;
	};

	const onpointerdown = (event: PointerEvent) => {
		event.preventDefault();
		handleMove(event);
		active = true;
		const target = event.target as HTMLElement;
		target.setPointerCapture(event.pointerId);
	};

	const onpointermove = (event: PointerEvent) => {
		if (!active) return;
		handleMove(event);
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
	class="relative cursor-col-resize overflow-hidden inline-block touch-pan-y rounded-md"
	on:pointerdown={onpointerdown}
	on:pointermove={onpointermove}
	on:pointerup={onpointerup}
	bind:this={container}
>
	<img
		src="/dog.jpg"
		alt=""
		draggable="false"
		style="clip-path: polygon(0 0, {percentage}% 0, {percentage}% 100%, 0 100%);"
	/>
	<img
		src="/dog-min.jpg"
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
