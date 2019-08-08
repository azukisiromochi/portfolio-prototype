<script>
	import Syubababa from '../components/Syubababa.svelte';
</script>

<style lang="scss">
	$gradient: linear-gradient(-90deg, #FF00A1, #F6FF00);

	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
		background-image: $gradient;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

<h1>Great success!</h1>

<Syubababa duration={"800ms"} delay={"700ms"} />
<Syubababa duration={"700ms"} delay={"1000ms"} height={"30vh"} />
<Syubababa duration={"600ms"} delay={"1200ms"} height={"20vh"} />
<Syubababa delay={"1400ms"} height={"10vh"} />
<Syubababa delay={"1500ms"} height={"25vh"} />

<figure>
	<img alt='Borat' src='great-success.png'>
	<figcaption>HIGH FIVE!</figcaption>
</figure>

<p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p>
