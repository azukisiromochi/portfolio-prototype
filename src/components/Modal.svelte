<script>
	import { createEventDispatcher } from 'svelte';
	import Syubababa from '../components/Syubababa.svelte';

	const dispatch = createEventDispatcher();
</script>

<style>
	.modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,0.3);
	}

	.modal {
		position: absolute;
		left: 50%;
		top: 50vh;
		width: calc(100vw - 4em);
		max-width: 32em;
		max-height: calc(100vh - 4em);
		overflow: auto;
		transform: translate(-50%,-50%);
		padding: 1em;
		border-radius: 0.2em;
		background: white;
	}

	button {
		display: block;
	}
</style>

<div class='modal-background' on:click='{() => dispatch("close")}'>
	<Syubababa duration={"800ms"} delay={"700ms"} />
	<Syubababa duration={"700ms"} delay={"1000ms"} height={"30vh"} />
	<Syubababa duration={"600ms"} delay={"1200ms"} height={"20vh"} />
	<Syubababa delay={"1400ms"} height={"10vh"} />
	<Syubababa delay={"1500ms"} height={"25vh"} />
</div>

<div class='modal'>
	<slot name='header'></slot>
	<hr>
	<slot></slot>
	<hr>

	<button on:click='{() => dispatch("close")}'>close modal</button>
</div>
