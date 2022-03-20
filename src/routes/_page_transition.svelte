<script>
  import { fly } from 'svelte/transition';
  import { quartIn, quartOut } from 'svelte/easing';
  import { page } from '$app/stores';

  import { navOpen } from '../js/stores.js';

  $: isHome = $page.url.pathname === '/';
</script>

{#if !$navOpen}
  <div
    class="page"
    class:isHome
    class:navOpen={$navOpen}
    in:fly={{ duration: 500, delay: 500, opacity: 0, y: -20, easing: quartOut }}
    out:fly={{ duration: 250, opacity: 0, y: 20, easing: quartIn }}
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
