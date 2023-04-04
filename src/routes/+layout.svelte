<script>
	import '../styles/app.css';
	import '../styles/fonts.css';
	import { writable } from 'svelte/store';
	let coords = writable({ x: 0, y: 0 });
	let size = writable(0);
</script>

<div
	id="app"
	class="absolute left-0 top-0 h-full w-full cursor-none overflow-hidden bg-black"
	on:mousemove={(e) => {
		coords.set({ x: e.clientX, y: e.clientY });
		size.set(12);
	}}
	on:mouseleave={() => size.set(0)}
>
	<slot />
</div>
<svg class="absolute h-full w-full">
	<circle
		class="ease transition-[r] duration-200"
		cx={$coords.x}
		cy={$coords.y}
		r={$size}
		fill="none"
		stroke="white"
		stroke-width={5}
	/>
</svg>
