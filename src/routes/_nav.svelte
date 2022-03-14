<script>
  import MenuToggle from './_menu_toggle.svelte';
  import { page } from '$app/stores';
  import { navOpen } from '../js/stores.js';

  const navItems = [
    { text: 'Expertise', href: '/expertise/' },
    { text: 'Experience', href: '/experience/' },
    { text: 'Education', href: '/education/' },
    { text: 'Etcetera', href: '/etcetera/' }
  ];
</script>

<header>
  <MenuToggle bind:open={$navOpen} />
  <nav class:navOpen={$navOpen}>
    <ul>
      <li
        class="home"
        class:active={$page.url.pathname === '/'}
        on:click={() => ($navOpen = false)}
      >
        <a sveltekit:prefetch href="/">Nick Vincent</a>
      </li>
      {#each navItems as item}
        <li>
          <a
            sveltekit:prefetch
            href={item.href}
            class:active={$page.url.pathname === item.href}
            on:click={() => ($navOpen = false)}>{item.text}</a
          >
        </li>
      {/each}
    </ul>
  </nav>
</header>

<style>
  nav {
    --duration: 0.5s;
    padding-bottom: 1em;
    margin-bottom: 2em;
    border-bottom: 0.1em solid var(--color-line);
    transition: transform var(--duration) var(--easing-standard),
      opacity var(--duration) var(--easing-standard),
      visibility var(--duration) var(--easing-standard), var(--dom-x-ray-transition);
  }

  @media print {
    nav {
      display: none;
    }
  }

  ul {
    display: flex;
    margin: 0;
    flex-wrap: wrap;
    list-style: none;
    column-gap: 1em;
    font-size: 0.75em;
  }

  li {
    display: block;
  }

  li::before {
    display: none;
  }

  .home {
    flex: 1 0 100%;
    font-size: 2em;
    line-height: 1.5em;
  }

  a {
    display: inline-block;
    font-weight: 600;
    letter-spacing: -0.025em;
    transition: transform var(--duration) var(--easing-standard),
      opacity var(--duration) var(--easing-standard),
      visibility var(--duration) var(--easing-standard), var(--dom-x-ray-transition);
  }

  a::after {
    display: none;
  }

  .home a {
    pointer-events: none;
    opacity: 0;
    visibility: hidden;
    font-weight: 700;
    color: var(--color-h1);
    transform: scale(0.95);
    transform-origin: center;
  }

  .home:not(.active) a {
    pointer-events: auto;
    opacity: 1;
    visibility: visible;
    transform: scale(1);
  }

  a {
    opacity: var(--receded-opacity);
  }

  a.active {
    opacity: 1;
  }

  nav:focus-within {
    opacity: 1;
  }

  a:focus-visible {
    opacity: 1;
    transform: scale(1.1);
  }

  .home a:focus-visible {
    opacity: 1;
    transform: scale(1.05);
  }

  @media (hover: hover) {
    nav {
      opacity: var(--receded-opacity);
    }

    nav:hover {
      opacity: 1;
    }

    a:hover {
      opacity: 1;
      transform: scale(1.1);
    }

    .home a:hover {
      opacity: 1;
      transform: scale(1.05);
    }
  }

  @media (max-width: 480px) {
    nav {
      pointer-events: none;
      position: fixed;
      margin: 0;
      padding: 4em 1em;
      opacity: 0;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      visibility: hidden;
      border-color: rgba(var(--color-line-rgb), 0);
      transform: scale(0.95);
    }

    nav.navOpen {
      pointer-events: auto;
      opacity: 1;
      visibility: visible;
      transform: scale(1);
      transition: transform var(--duration) var(--easing-standard) var(--duration),
        opacity var(--duration) var(--easing-standard) var(--duration),
        visibility var(--duration) var(--easing-standard) var(--duration),
        var(--dom-x-ray-transition);
    }

    ul {
      align-content: center;
      row-gap: 0;
      height: 100%;
      font-size: 1.5em;
      line-height: 1.5em;
      text-align: center;
    }

    li {
      flex: 1 0 100%;
    }

    .home {
      font-size: 1.25em;
    }

    nav.navOpen .home a,
    nav.navOpen .home.active a {
      opacity: 1;
      visibility: visible;
    }

    nav:not(.navOpen) a,
    nav:not(.navOpen) .home a {
      pointer-events: none;
      opacity: 0;
      visibility: hidden;
    }
  }
</style>
