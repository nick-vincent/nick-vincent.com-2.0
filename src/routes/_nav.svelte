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
      <li class="home">
        <a
          href="/"
          sveltekit:prefetch
          class:active={$page.url.pathname === '/'}
          on:click={() => ($navOpen = false)}>Nick Vincent</a
        >
      </li>
      {#each navItems as item}
        <li>
          <a
            href={item.href}
            sveltekit:prefetch
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
    position: relative;
    padding-bottom: 1em;
    transition: transform var(--duration) var(--easing-standard),
      opacity var(--duration) var(--easing-standard),
      visibility var(--duration) var(--easing-standard), var(--dom-x-ray-transition);
  }

  @media (min-width: 481px) {
    nav::before,
    nav::after {
      content: '';
      pointer-events: none;
      z-index: 0;
      display: block;
      position: absolute;
      width: 100%;
      height: 100%;
      left: 0;
      top: 0;
      background-repeat: no-repeat;
      background-position: top left, bottom left;
      background-size: 100% 100%, 100% 0.1em;
      transition: opacity var(--color-transition), var(--dom-x-ray-transition);
    }

    nav::before {
      opacity: var(--light-gradient-opacity);
      background-image: var(--light-nav-bg-image);
    }

    nav::after {
      opacity: var(--dark-gradient-opacity);
      background-image: var(--dark-nav-bg-image);
    }
  }

  @media print {
    nav {
      display: none;
    }
  }

  ul {
    display: flex;
    margin: 0;
    padding: 0;
    flex-wrap: wrap;
    justify-content: center;
    list-style: none;
    column-gap: 0.75em;
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
    text-align: center;
  }

  a {
    display: inline-block;
    font-weight: 600;
    letter-spacing: -0.025em;
    opacity: var(--receded-opacity);
    transition: transform var(--duration) var(--easing-standard),
      opacity var(--duration) var(--easing-standard),
      visibility var(--duration) var(--easing-standard), var(--dom-x-ray-transition);
  }

  a::after {
    display: none;
  }

  a.active {
    opacity: 1;
  }

  .home a {
    font-weight: 700;
    color: var(--color-heading);
  }

  .home a.active {
    pointer-events: none;
    opacity: 0;
    visibility: hidden;
    transform: scale(0.95);
  }

  nav:focus-within {
    opacity: 1;
  }

  a:focus-visible {
    opacity: 1;
    transform: scale(1.1);
  }

  .home a:focus-visible {
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

    .home a {
      opacity: 1;
    }

    nav.navOpen .home a.active {
      pointer-events: auto;
      opacity: 1;
      visibility: visible;
    }
  }
</style>
