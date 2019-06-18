<script>
	const layers = [0, 1, 2, 3, 4, 5, 6];

	let y;
</script>

<svelte:window bind:scrollY={y}/>

<div class="portfolio-container">
	{#each [0, 1, 2, 3, 4, 5, 6] as layer}
		<img
			style="transform: translate(0,{-y * layer / (layers.length - 1)}px); top: {700 * layer}px"
			src="./images/layer-{layer}.png"
			alt="portfolio layer {layer}"
		>
	{/each}
</div>

<div class="text">
	<span style="opacity: {1 - Math.max(0, y / 40)}">
		scroll down
	</span>

	<div class="foreground">
		You have scrolled {y} pixels
	</div>
</div>

<style>
	.portfolio-container {
		position: fixed;
		width: 2400px;
		height: 712px;
		left: 50%;
		transform: translate(-50%,0);
	}

	.portfolio-container img {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		will-change: transform;
	}

	.portfolio-container img:last-child::after {
		content: '';
		position: absolute;
		width: 100%;
		height: 100%;
		background: #F5B090;
	}

	.text {
		position: relative;
		width: 100%;
		height: 300vh;
		color: rgb(220,113,43);
		text-align: center;
		padding: 4em 0.5em 0.5em 0.5em;
		box-sizing: border-box;
		pointer-events: none;
	}

	span {
		display: block;
		font-size: 1em;
		text-transform: uppercase;
		will-change: transform, opacity;
	}

	.foreground {
		position: absolute;
		top: 5800px;
		left: 0;
		width: 100%;
		height: calc(100% - 712px);
		background-color: #F5B090;
		color: white;
		padding: 50vh 0 0 0;
	}

	:global(body) {
		margin: 0;
		padding: 0;
		background-color: #F5B090;
	}
</style>
