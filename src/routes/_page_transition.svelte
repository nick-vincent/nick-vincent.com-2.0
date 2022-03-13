<script>
  import { scale } from 'svelte/transition';
  import { cubicIn, cubicOut } from 'svelte/easing';
</script>

<div
  in:scale={{ duration: 500, delay: 500, opacity: 0, start: 0.95, easing: cubicOut }}
  out:scale={{ duration: 250, opacity: 0, start: 0.95, easing: cubicIn }}
>
  <slot />
</div>

<style>
  div {
    transform-origin: top center;
  }
</style>
