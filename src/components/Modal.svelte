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

		animation-name:fade-in-modal;
	  animation-duration:2s;
	  animation-timing-function: ease-out;
	  animation-delay:1s;
		animation-fill-mode: forwards;
		opacity: 0;
	}

	button {
		display: block;
	}

	@keyframes fade-in-modal {
	  0% { opacity: 0; transform: translate3d(-100%, -50%, 0); }
	  100% { opacity: 1; transform: translate3d(-50%, -50%, 0); }
	}
</style>

<div class='modal-background' on:click='{() => dispatch("close")}'>
	<Syubababa duration={"800ms"} delay={"300ms"} />
	<Syubababa duration={"700ms"} delay={"600ms"} height={"30vh"} />
	<Syubababa duration={"600ms"} delay={"800ms"} height={"20vh"} />
	<Syubababa delay={"1000ms"} height={"10vh"} />
	<Syubababa delay={"1100ms"} height={"25vh"} />
</div>

<div class='modal'>
	<slot name='header'></slot>
	<hr>
	<slot></slot>
	<hr>

	<button on:click='{() => dispatch("close")}'>close modal</button>
</div>
