<script>
  // Set style `animation-duration` (default: 800ms)
	export let duration = '';
  // Set style `animation-delay` (default: 0)
  export let delay = '';
  // Set style `height` (default: 15vh)
  export let height = '';

</script>

<style lang="scss">
div {
  background: #96fbc4;
  height: 15vh;
  width: 10vw;
  margin-left: -15vw;
	animation-name: fadeIn;
  animation-duration: 800ms;
  animation-timing-function: ease;
  // animation-iteration-count: 1;
  animation-fill-mode:forwards;
}

@keyframes fadeIn {
  25% {
    background: #f9f586;
  }
  50% {
    transform: scaleX(10) skew(-30deg);
    transform-origin: 0% 50%;
    background: #96fbc4;
  }
  75% {
    border-radius: 30% 20% / 45% 15%;
    background: #fe9a8b;
  }
  99% {
    box-shadow: -20px 10px 10px 10px rgba(0,0,0,.8);
  }
  100% {
    transform: translatex(150vw) scaleX(1) skew(0deg);
    transform-origin: 0% 50%;
    background: #fe9a8b;
    margin-left: 0;
  }
}
</style>

<div style="animation-duration: {duration}; animation-delay: {delay}; height: {height}"/>
