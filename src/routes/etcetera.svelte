<script>
  import { afterUpdate } from 'svelte';
  import DarkMode from 'svelte-dark-mode';

  let theme = 'light';

  $: switchTheme = theme === 'dark' ? 'light' : 'dark';

  afterUpdate(() => {
    document.documentElement.classList.add(theme);
    document.documentElement.classList.remove(switchTheme);
  });
</script>

<svelte:head>
  <title>Nick Vincent: Etcetera</title>
  <meta name="description" content="Fluent in design and code" />
</svelte:head>

<DarkMode bind:theme />

<h1>Etcetera</h1>

<p>
  I made <a
    href="https://chrome.google.com/webstore/detail/dom-x-ray/olfkgegmjhgehnakignkabhbdchkhnkj"
    rel="external"
    target="_blank">DOM X-Ray</a
  ><br />
  a dev tool to see<br />
  through the DOM
</p>

<p>I’m also known to:</p>
<ul>
  <li>
    <a href="https://instagram.com/im.still.in.beta/" rel="external" target="_blank">make faces</a>
  </li>
  <li>
    <a href="https://instagram.com/the.nick.vincent/" rel="external" target="_blank">snap photos</a>
  </li>
  <li>
    <a href="https://youtube.com/sixftdwarf" rel="external" target="_blank">strum tunes</a>
  </li>
  <li>
    <a href="https://annumford.com" rel="external" target="_blank">pen odes</a>
  </li>
</ul>

<p>This webpage features:</p>
<ul>
  <li>
    <a href="https://svelte.dev" rel="external" target="_blank">svelte</a>
  </li>
  <li>
    <a href="https://css-tricks.com/snippets/css/system-font-stack/" rel="external" target="_blank"
      >system fonts</a
    >
  </li>
  <li>
    <a href="https://css-tricks.com/dark-modes-with-css/" rel="external" target="_blank"
      >dark mode</a
    >
  </li>
</ul>

<p>While you’re here, you can:</p>
<ul>
  <li>
    <button on:click={() => document.documentElement.classList.toggle('dom-x-ray')}
      >demo DOM X-Ray</button
    >
  </li>
  <li><button on:click={() => (theme = switchTheme)}>toggle dark mode</button></li>
</ul>
