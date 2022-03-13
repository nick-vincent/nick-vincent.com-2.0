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
</style>
