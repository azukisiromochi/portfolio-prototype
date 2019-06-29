<script>
	import Stars from '../components/Stars.svelte';
	import Rainy from '../components/Rainy.svelte';
	import Modal from '../components/Modal.svelte';

	let showModal = false;

	const random = Math.floor(Math.random() * 2);
	const neonColor = !!random ? 'neon1' : 'neon3';

	console.log(random);

	const layers = [0, 1, 2, 3, 4, 5, 6];
	let y;
</script>

<svelte:window bind:scrollY={y}/>

<div class="portfolio-container">
	{#if !!random}<Rainy/>{/if}
	{#if !random}<Stars/>{/if}
	{#each [0, 1, 2, 3, 4, 5, 6] as layer}
		<img
			style="transform: translate(0,{-y * (layer + 1) / (layers.length)}px); top: {700 * (layer + 1)}px"
			src="./images/layer-{layer}.png"
			alt="portfolio layer {layer}"
		>
	{/each}
</div>
<div class="neon-wrapper">
  <div class="neon-items">
		<a
			on:click="{() => showModal = true}"
			class="neon {neonColor}"
			style="opacity: {1 - Math.max(0, y / 400)}">modal</a>
	</div>
</div>

<div class="text">
	<div class="foreground">
		You have scrolled {y} pixels
	</div>
</div>

{#if showModal}
	<Modal on:close="{() => showModal = false}">
		<h2 slot="header">
			modal
			<small><em>adjective</em>  mod·al \ˈmō-dəl\</small>
		</h2>

		<ol class="definition-list">
			<li>of or relating to modality in logic</li>
			<li>containing provisions as to the mode of procedure or the manner of taking effect —used of a contract or legacy</li>
			<li>of or relating to a musical mode</li>
			<li>of or relating to structure as opposed to substance</li>
			<li>of, relating to, or constituting a grammatical form or category characteristically indicating predication</li>
			<li>of or relating to a statistical mode</li>
		</ol>

		<a href="https://www.merriam-webster.com/dictionary/modal">merriam-webster.com</a>
	</Modal>
{/if}

<style lang="scss">
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
		text-align: center;
		padding: 4em 0.5em 0.5em 0.5em;
		box-sizing: border-box;
		pointer-events: none;
	}

	.foreground {
		position: absolute;
		top: 5523px;
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
	}

	:global(*),
	:global(*:before),
	:global(*:after) {
	  box-sizing: border-box;
	}

	/***********************
	* IMPORTS
	* VARIABLES
	* MIXINS
	***********************/
	@import url('https://fonts.googleapis.com/css?family=Megrim');

	$neon1color: cyan;
	$neon2color: yellow;
	$neon3color: magenta;
	$neon4color: #83ff00;

	@mixin neonAnimation($color) {
	  0%, 11%, 13%, 17%, 19%, 100%  {
	    text-shadow: 0px 0px 15px $color;
	  }

	  12%, 18% {
	    text-shadow: 0 0 0px #fff;
	  }
	}

	@mixin newKeyframes($animationName) {
	  @-webkit-keyframes #{$animationName} {
	    @content;
	  }
	  @keyframes #{$animationName} {
	    @content;
	  }
	}

	/***********************
	* STRUCTURAL
	***********************/
	.neon-wrapper {
	  align-items: center;
	  // background-color: #111;
	  display: flex;
	  flex-direction: column;
	  height: 100vh;
	  justify-content: center;
	  width: 100vw;
	}

	.neon-items {
	  display: inline-block;
	  position: relative;
	  text-align: center;
	}

	/***********************
	* NEON VARIABLES
	***********************/
	.neon1 {
	  --animation: neon1;
	  --color: #{$neon1color};
	  --radial-bg: radial-gradient( #{transparentize($neon1color, .8)} 10%, transparent 45%);
	}

	.neon2 {
	  --animation: neon2;
	  --color: #{$neon2color};
	  --radial-bg: radial-gradient( #{transparentize($neon2color, .8)} 10%, transparent 45%);
	}

	.neon3 {
	  --animation: neon3;
	  --color: #{$neon3color};
	  --radial-bg: radial-gradient( #{transparentize($neon3color, .8)} 20%, transparent 60%);
	}

	.neon4 {
	  --animation: neon4;
	  --color: #{$neon4color};
	  --radial-bg: radial-gradient( #{transparentize($neon4color, .8)} 20%, transparent 60%);
	}


	/***********************
	* NEON
	***********************/
	.neon {
	  color: var(--color);
	  display: block;
	  font-family: 'Megrim', cursive;
	  font-size: 60px;
	  letter-spacing: 2px;
	  opacity: .6;
	  position: relative;
	  text-decoration: none;
	  text-transform: uppercase;
	  transition: 130ms cubic-bezier(.4, 1, .8, 1.8);
	  // z-index: 1;
		cursor: pointer;

	  &::before {
      bottom: 50%;
      content: '';
      left: 50%;
      position: absolute;
      right: 50%;
      top: 50%;
      // z-index: -1;
	  }

	  &:hover {
	    animation: var(--animation) 2s forwards;
	    letter-spacing: 10px;
	    text-indent: 10px;
	    opacity: 1;

	    &::before {
	      background: var(--radial-bg);
	      bottom: -50%;
	      left: -50%;
	      pointer-events: none;
	      right: -50%;
	      top: -50%;
	    }
	  }
	}

	/***********************
	* ANIMATIONS
	***********************/
	@include newKeyframes(neon1) {
	  @include neonAnimation($neon1color);
	};

	@include newKeyframes(neon2) {
	  @include neonAnimation($neon2color);
	};

	@include newKeyframes(neon3) {
	  @include neonAnimation($neon3color);
	};

</style>
