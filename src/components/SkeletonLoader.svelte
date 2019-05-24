<script>
  import SkeletonLoaderBlock from './SkeletonLoaderBlock.svelte';
  import SkeletonLoaderString from './SkeletonLoaderString.svelte';

  export let type = 'string';
  export let animated = true;
  export let background;
  export let animatedColor;
  export let width;
  export let height;
  export let count;
  export let fontSize;
</script>

<style>

</style>

{#if type === 'string'}
  <SkeletonLoaderString {animated} {background} {animatedColor} {width} {height} {count} {fontSize} />
{:else if type === 'block'}
  <SkeletonLoaderBlock {animated} {background} {animatedColor} {width} {height} />
{/if}