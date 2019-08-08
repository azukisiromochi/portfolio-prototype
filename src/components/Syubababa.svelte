<script>
  // Set style `animation-duration` (default: 800ms)
	export let duration = '';
  // Set style `animation-delay` (default: 0)
  export let delay = '';
  // Set style `height` (default: 15vh)
  export let height = '';

</script>

<style lang="scss">
$color1: #e1315b;
$color2: #f47d4a;
$color3: #ffff42;
$color4: #00cffa;

div {
  background: $color1;
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
  15% { background: $color1; }
	30% { background: $color2; }
	45% { background: $color3; }
  50% {
    transform: scaleX(15) skew(-30deg);
    transform-origin: 0% 50%;
  }
  75% { border-radius: 30% 20% / 40% 15%; }
	80% { background: $color4; }
  90% { box-shadow: -20px 10px 10px 10px rgba(0, 0, 0, .8); }
  100% {
    transform: translatex(120vw) scaleX(2) skew(0deg);
    transform-origin: 0% 50%;
    margin-left: 0;
  }
}
</style>

<div style="animation-duration: {duration}; animation-delay: {delay}; height: {height}"/>
