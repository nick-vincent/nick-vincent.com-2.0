<script lang="ts">
  import { afterUpdate, onMount } from 'svelte';
  import DarkMode from 'svelte-dark-mode';
  import { theme } from '../js/stores.js';
  import '../css/app.css';

  import Header from './_header.svelte';
  import Expertise from './_expertise.svelte';
  import Experience from './_experience.svelte';
  import Education from './_education.svelte';
  import Footer from './_footer.svelte';

  $: switchTheme = $theme === 'dark' ? 'light' : 'dark';

  let wrapper;

  afterUpdate(() => {
    document.documentElement.classList.add($theme);
    document.documentElement.classList.remove(switchTheme);
  });

  onMount(() => {
    setTimeout(() => wrapper.classList.remove('loading'), 1);
  });
</script>

<svelte:head>
  <title>Nick Vincent: Fluent in both design & code</title>
</svelte:head>

<DarkMode bind:theme={$theme} />

<div bind:this={wrapper} class="wrapper loading">
  <Header />
  <main>
    <Expertise />
    <Experience />
    <Education />
  </main>
  <Footer />
</div>

<style>
  @media print, (min-width: 50rem) {
    .wrapper {
      display: grid;
      gap: var(--grid-margin);
    }

    main {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      grid-template-rows: max-content;
      gap: var(--grid-margin);
    }
  }

  .loading {
    opacity: 0;
    filter: blur(1rem);
    transform: translateY(-1rem);
  }
</style>
