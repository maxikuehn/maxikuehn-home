<script>
	export let color = '#ff9b51';
	export let size = 60;
	export let unit = 'px';
	export let duration = 1;
	export let durationUnit = 'ms';
</script>

<div
	class="wrapper"
	style="--size: {size}{unit}; --color: {color}; --duration: {duration}{durationUnit};"
>
	{#each [1, 2, 3] as version}
		<div class="circle" style="animation-delay: {(duration / 3) * (version - 1) + durationUnit};" />
	{/each}
</div>

<style>
	.wrapper {
		width: var(--size);
		height: var(--size);
	}
	.circle {
		border-radius: 100%;
		animation-fill-mode: both;
		position: absolute;
		opacity: 0;
		width: var(--size);
		height: var(--size);
		background-color: var(--color);
		animation: bounce var(--duration) linear infinite;
	}
	@keyframes bounce {
		0% {
			opacity: 0;
			transform: scale(0);
		}
		5% {
			opacity: 1;
		}
		100% {
			opacity: 0;
			transform: scale(1);
		}
	}
</style>
