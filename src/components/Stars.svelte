<style lang="scss">

  #stars-background {
    background: url('../images/foreground.png') 5% 5%, url('../images/midground.png') 50% 50%, url('../images/background.png') 90% 110%;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    position: absolute;
    -webkit-transition: left 300s linear;
    -moz-transition: left 300s linear;
    -o-transition: left 300s linear;
    -ms-transition: left 300s linear;
    transition: left 300s linear;
  }

  #stars {
    &:target #stars-background {
      left: -5000px;
    }

    &:hover #stars-background {
      left: -9999px;
    }
  }

</style>

<div id="stars">
    <div id="stars-background"></div>
</div>
