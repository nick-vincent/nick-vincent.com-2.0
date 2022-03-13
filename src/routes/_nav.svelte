<script>
  import { page } from '$app/stores';

  const navItems = [
    { text: 'Expertise', href: '/expertise/' },
    { text: 'Experience', href: '/experience/' },
    { text: 'Education', href: '/education/' },
    { text: 'Etcetera', href: '/etcetera/' }
  ];

  $: isHome = $page.url.pathname === '/' ? true : false;
</script>

<header>
  <nav>
    <ul>
      <li class="home" class:active={$page.url.pathname === '/'}>
        <a sveltekit:prefetch href="/">Nick Vincent</a>
      </li>
      {#each navItems as item}
        <li>
          <a sveltekit:prefetch href={item.href} class:active={$page.url.pathname === item.href}
            >{item.text}</a
          >
        </li>
      {/each}
    </ul>
  </nav>
</header>

<style>
  nav {
    --duration: 0.5s;
    --easing: var(--easing-standard);
    --receded-opacity: 0.5;
    padding-bottom: 1em;
    margin-bottom: 2em;
    border-bottom: 0.1em solid var(--color-line);
    transition: opacity var(--duration) var(--easing), var(--dom-x-ray-transition);
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
    letter-spacing: -0.025em;
  }

  a {
    display: inline-block;
    font-weight: 600;
    transition: transform var(--duration) var(--easing), opacity var(--duration) var(--easing),
      var(--dom-x-ray-transition);
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
    transition: transform var(--duration) var(--easing), opacity var(--duration) var(--easing),
      visibility var(--duration) var(--easing), var(--dom-x-ray-transition);
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

  @media (hover: hover) {
    nav {
      opacity: var(--receded-opacity);
    }

    nav:hover,
    nav:focus-within {
      opacity: 1;
    }

    a:not(.active):hover,
    a:focus-visible {
      opacity: 1;
      transform: scale(1.1);
    }

    .home:not(.active) a:hover,
    .home:not(.active) a:focus-visible {
      opacity: 1;
      transform: scale(1.05);
    }
  }
</style>
