<script>
	const droplets = Array(250);
</script>

<div class="rain">
	{#each droplets as droplet}
    <svg
      class="rain__drop"
      preserveAspectRatio="xMinYMin"
      viewBox="0 0 5 50"
      style="
				z-index: 5;
				--x: {Math.floor(Math.random() * 100)};
				--y: {Math.floor(Math.random() * 100)};
				--o: {Math.random()};
				--a: {Math.random() + 0.5};
				--d: {(Math.random() * 2) - 1};
				--s: {Math.random()};">
			<defs>
		    <linearGradient id="gradient">
		      <stop class="stop1" offset="0%"/>
		      <stop class="stop2" offset="100%"/>
		    </linearGradient>
		  </defs>
			<path
	      stroke="none"
	      d="M 2.5,0 C 2.6949458,3.5392017 3.344765,20.524571 4.4494577,30.9559 5.7551357,42.666753 4.5915685,50 2.5,50 0.40843152,50 -0.75513565,42.666753 0.55054234,30.9559 1.655235,20.524571 2.3050542,3.5392017 2.5,0 Z">
	    </path>
		</svg>
	{/each}
</div>

<style lang="scss">
	.rain {
		background: linear-gradient(to top, #e2c9cc 0%, #e7627d 7%, #b8235a 15%, #801357 30%, #3d1635 55%, #1c1a27 100%);
		width: 100%;
		height: 100%;
	}
	.rain__drop {
		-webkit-animation-delay: calc(var(--d) * 1s);
						animation-delay: calc(var(--d) * 1s);
		-webkit-animation-duration: calc(var(--a) * 1s);
						animation-duration: calc(var(--a) * 1s);
		-webkit-animation-iteration-count: infinite;
						animation-iteration-count: infinite;
		-webkit-animation-name: drop;
						animation-name: drop;
		-webkit-animation-timing-function: linear;
						animation-timing-function: linear;
		height: 30px;
		left: calc(var(--x) * 1%);
		position: absolute;
		top: calc((var(--y) + 50) * -1px);

		path {
			fill: url("#gradient");
			opacity: var(--o);
			-webkit-transform: scaleY(calc(var(--s) * 1.5));
							transform: scaleY(calc(var(--s) * 1.5));
		}

		.stop1 {
			stop-color: #22c1c3;
		}
		.stop2 {
			stop-color: #fdbb2d;
			stop-opacity: 0;
		}
	}

	@-webkit-keyframes drop {
		90% {
			opacity: 1;
		}
		100% {
			opacity: 0;
			-webkit-transform: translateY(100vh);
							transform: translateY(100vh);
		}
	}
	@keyframes drop {
		90% {
			opacity: 1;
		}
		100% {
			opacity: 0;
			-webkit-transform: translateY(100vh);
							transform: translateY(100vh);
		}
	}
</style>
