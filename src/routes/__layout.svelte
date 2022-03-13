<script lang="ts">
  import { afterUpdate, onMount } from 'svelte';
  import DarkMode from 'svelte-dark-mode';
  import Nav from './_nav.svelte';
  import { theme } from '../js/stores.js';
  import '../css/app.css';

  $: switchTheme = $theme === 'dark' ? 'light' : 'dark';

  afterUpdate(() => {
    document.documentElement.classList.add($theme);
    document.documentElement.classList.remove(switchTheme);
  });

  onMount(() => {
    document.documentElement.classList.add('loaded');
  });
</script>

<DarkMode bind:theme={$theme} />

<Nav />

<main>
  <slot />
</main>

<style>
  main {
    flex: 1 0 100%;
  }
</style>
