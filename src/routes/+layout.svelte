<script>
	import '../styles/app.css';
	import '../styles/fonts.css';
	import { writable } from 'svelte/store';
	let coords = writable({ x: 0, y: 0 });
	let size = writable(0);
</script>

<div
	on:mousemove={(e) => coords.set({ x: e.clientX, y: e.clientY })}
	on:mouseenter={() => {
		size.set(10);
	}}
	on:mouseleave={() => size.set(0)}
>
	<slot />
</div>
<svg>
	<circle cx={$coords.x} cy={$coords.y} r={$size} />
</svg>

<style>
	div {
		position: absolute;
		overflow: hidden;
		width: 100%;
		height: 100%;
		background: #000;
		cursor: none;
		/* border: 1px solid red; */
	}
	svg {
		position: absolute;
		width: 100%;
		height: 100%;
	}
	circle {
		fill: none;
	}
	@media (hover: hover) and (pointer: fine) {
		circle {
			stroke: #000;
			stroke-width: 4;
		}
	}
</style>
