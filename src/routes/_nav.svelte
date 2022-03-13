<script>
  const navItems = [
    { text: 'Nick Vincent', href: '/' },
    { text: 'Expertise', href: '/expertise/' },
    { text: 'Experience', href: '/experience/' },
    { text: 'Education', href: '/education/' },
    { text: 'Etcetera', href: '/etcetera/' }
  ];
</script>

<nav>
  <ul>
    {#each navItems as item}
      <li>
        <a sveltekit:prefetch href={item.href}>{item.text}</a>
      </li>
    {/each}
  </ul>
</nav>

<style>
  ul {
    display: flex;
    list-style: none;
    gap: 1em;
  }

  li {
    display: block;
  }

  li::before {
    display: none;
  }
</style>
