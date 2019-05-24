<script>
  export let animated = true;
  export let background = '#eee';
  export let animatedColor = '#fcfcfc';
  export let width;
  export let height;
</script>

<style>
  .wrapper {
    width: 100%;
    height: 100px;
    display: block;
  }

  .loader {
    position: relative;
    display: block;
    width: 100%;
    height: 100%;
    background-color: #eee;
    border-radius: 4px;
    overflow: hidden;
  }
  .animate {
    content: '';
    position: absolute;
    top: -100%;
    left: 0;
    width: 15px;
    height: calc(100% * 2);
    filter: blur(15px);
    background-color: #fcfcfc;
    /* box-shadow: 0px 0px 60px 10px #fcfcfc; */
    transform: rotate(15deg);
    animation: animate .7s linear infinite;
  }

  @keyframes animate {
    0%{
      left: 0;
      top: -100%;
    }
    50%{
      left: 50%;
      top: -50%;
    }
    100%{
      left: 100%;
      top: 0%;
    }
  }

</style>

<span class="wrapper" style="width: {width}; height: {height};">
  <span class="loader" style="background-color: {background};">
    {#if animated }
      <div class="animate" style="background-color: {animatedColor};"></div>
    {/if}
  </span>
</span>