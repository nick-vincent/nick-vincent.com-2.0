<script>
  import { scale } from 'svelte/transition';
  import { sineIn, sineOut } from 'svelte/easing';
</script>

<div
  in:scale={{ duration: 250, delay: 500, opacity: 0, start: 0.95, easing: sineOut }}
  out:scale={{ duration: 250, opacity: 0, start: 0.95, easing: sineIn }}
>
  <slot />
</div>

<style>
  div {
    transform-origin: top center;
  }
</style>
