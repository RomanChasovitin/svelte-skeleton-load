<script>
  export let animated = true;
  export let background = '#eee';
  export let animatedColor = '#fcfcfc';
  export let width = '100%';
  export let height = '16px';
  export let count = 1;
  export let fontSize = '16px';
  const arr = new Array();
  arr.length = count;
  console.log(arr);
</script>

<style>
  .wrapper {
    width: 100%;
    display: block;
    margin-bottom: 8px;
  }

  .wrapper:last-child{
    margin-bottom: 0;
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

{#each arr as str }
  <span class="wrapper" style="width: {width}; height: {fontSize};">
    <span class="loader" style="background-color: {background};">
      {#if animated }
        <div class="animate" style="background-color: {animatedColor};"></div>
      {/if}
    </span>
  </span>
{/each}