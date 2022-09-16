<script>
	import Jumper from '../components/Jumper.svelte';

	const colorOptions = [
		'#f94144',
		'#f3722c',
		'#f8961e',
		'#f9c74f',
		'#90be6d',
		'#43aa8b',
		'#577590'
	];
	let color = colorOptions[Math.floor(Math.random() * colorOptions.length)];

	let innerHeight = 0;
	let innerWidth = 0;

	$: size = 1.5 * Math.max(innerHeight, innerWidth);
	$: duration = Math.floor(size) * 4;
</script>

<svelte:window bind:innerHeight bind:innerWidth />

<div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 overflow-hidden">
	<Jumper {size} {color} {duration} />
</div>
<div class="absolute w-full h-full py-5 z-10  flex justify-center">
	<div class="h-full flex flex-col justify-between overflow-hidden">
		<p>diese Seite ist noch im Aufbau</p>
		<p>schau doch später nochmal vorbei</p>
	</div>
</div>

<style>
	p {
		font-size: x-large;
		font-family: JetBrainsMono;
		text-align: center;
		transition: all 0.3s ease-in-out;
		max-width: 50vw;
		user-select: none;
	}
	@media (hover: hover) and (pointer: fine) {
		/* desktop */
		p:hover {
			word-spacing: 1.7rem;
			letter-spacing: 2rem;
			font-size: min(6vw, 150px);
		}
	}
	@media (hover: none) and (pointer: coarse) {
		/* mobile */
		p:active {
			font-size: min(12vw, 50px);
		}
	}
</style>
