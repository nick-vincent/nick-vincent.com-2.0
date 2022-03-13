<script lang="ts">
  import { onMount } from 'svelte';
  import Nav from './_nav.svelte';
  import '../app.css';

  onMount(() => {
    document.documentElement.classList.add('loaded');
  });
</script>

<Nav />

<main>
  <slot />
</main>

<style>
  main {
    flex: 1 0 100%;
  }
</style>
