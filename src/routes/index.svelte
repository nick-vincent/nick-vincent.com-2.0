<script>
  import PageTransition from './_page_transition.svelte';
</script>

<svelte:head>
  <title>Nick Vincent: Fluent in design and code</title>
</svelte:head>

<PageTransition>
  <a href="/nick-vincent.jpg" class="image-link" target="_blank"
    ><img alt="Nick Vincent" src="/nick-vincent.jpg" width="640" height="640" /></a
  >
  <h1>Nick Vincent</h1>
  <p>
    Fluent in both design&nbsp;&&nbsp;code<br />
    Prefers work to speak&nbsp;for&nbsp;itself<br />
    <a rel="external" target="_blank" href="mailto:the.nick.vincent@gmail.com"
      >the.nick.vincent@gmail.com</a
    >
  </p>
</PageTransition>

<style>
  p {
    margin: 0;
  }

  img {
    display: inline-block;
    width: 8em;
    height: auto;
    border-radius: 50%;
  }

  .image-link {
    display: inline-block;
    transform-origin: center;
    transition: transform 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55) 0.05s;
  }

  .image-link::after {
    display: none;
  }

  .image-link:focus {
    transform: translate3d(0, 0, 0) scale(1.05) rotate(15deg);
  }

  @media (hover: hover) {
    .image-link:hover {
      transform: translate3d(0, 0, 0) scale(1.05) rotate(15deg);
    }
  }
</style>
