<script>
  import { scale } from 'svelte/transition';
  import { cubicIn, cubicOut } from 'svelte/easing';

  import { navOpen } from '../js/stores.js';
</script>

{#if !$navOpen}
  <div
    class:navOpen={$navOpen}
    in:scale={{ duration: 500, delay: 500, opacity: 0, start: 0.95, easing: cubicOut }}
    out:scale={{ duration: 250, opacity: 0, start: 0.95, easing: cubicIn }}
  >
    <slot />
  </div>
{/if}

<style>
  div {
    transform-origin: top center;
  }
</style>
