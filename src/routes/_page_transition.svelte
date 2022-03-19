<script>
  import { scale } from 'svelte/transition';
  import { cubicIn, cubicOut } from 'svelte/easing';
  import { page } from '$app/stores';

  import { navOpen } from '../js/stores.js';

  $: isHome = $page.url.pathname === '/';
</script>

{#if !$navOpen}
  <div
    class="page"
    class:isHome
    class:navOpen={$navOpen}
    in:scale={{ duration: 500, delay: 500, opacity: 0, start: 0.95, easing: cubicOut }}
    out:scale={{ duration: 250, opacity: 0, start: 0.95, easing: cubicIn }}
  >
    <slot />
  </div>
{/if}

<style>
  .page {
    transform-origin: top center;
  }

  @media (max-width: 480px) {
    .isHome {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
      min-height: 100%;
    }
  }
</style>
