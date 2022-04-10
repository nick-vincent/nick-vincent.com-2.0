<script>
  import { theme } from '../js/stores.js';

  $: switchTheme = $theme === 'dark' ? 'light' : 'dark';
</script>

<footer>
  <h2>Etcetera</h2>

  <div class="column">
    <p>
      I made
      <a
        href="https://chrome.google.com/webstore/detail/dom-x-ray/olfkgegmjhgehnakignkabhbdchkhnkj"
        rel="external"
        target="_blank">DOM X-Ray</a
      ><br />
      a dev tool to see<br />
      through the DOM
    </p>
  </div>

  <div class="column">
    <p>I’m also known to:</p>
    <ul>
      <li>
        <a href="https://instagram.com/im.still.in.beta/" rel="external" target="_blank"
          >make faces</a
        >
      </li>
      <li>
        <a href="https://instagram.com/the.nick.vincent/" rel="external" target="_blank"
          >snap photos</a
        >
      </li>
      <li>
        <a href="https://youtube.com/sixftdwarf" rel="external" target="_blank">strum tunes</a>
      </li>
      <li>
        <a href="https://annumford.com" rel="external" target="_blank">pen odes</a>
      </li>
    </ul>
  </div>

  <div class="column">
    <p>This website features:</p>
    <ul class="bullet">
      <li><a href="https://svelte.dev" rel="external" target="_blank">svelte</a></li>
      <li>
        <a
          href="https://css-tricks.com/snippets/css/complete-guide-grid/"
          rel="external"
          target="_blank">CSS grids</a
        >
      </li>
      <li>
        <a
          href="https://css-tricks.com/snippets/css/system-font-stack/"
          rel="external"
          target="_blank">system fonts</a
        >
      </li>
      <li>
        <a href="https://css-tricks.com/dark-modes-with-css/" rel="external" target="_blank"
          >dark mode</a
        >
      </li>
    </ul>
  </div>

  <div class="column">
    <p>While you’re here:</p>
    <ul>
      <li>
        <button on:click={() => document.documentElement.classList.toggle('dom-x-ray')}
          >demo DOM X-Ray</button
        >
      </li>
      <li><button on:click={() => ($theme = switchTheme)}>toggle dark mode</button></li>
      <li><button on:click={() => window.print()}>print this page</button></li>
    </ul>
  </div>
</footer>

<style>
  @media print, (min-width: 50rem) {
    footer {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr 1fr;
      grid-template-rows: max-content;
      gap: var(--grid-margin);
    }

    h2 {
      grid-column: span 4;
      margin: 0;
    }
  }

  ul {
    margin-top: -1rem;
  }
</style>
