<script>
  import PageTransition from './_page_transition.svelte';
</script>

<svelte:head>
  <title>Nick Vincent: Fluent in design and code</title>
</svelte:head>

<PageTransition>
  <div>
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
  </div>
</PageTransition>

<style>
  div {
    text-align: center;
  }

  h1 {
    margin: -0.125em 0 0;
  }

  p {
    margin: 0;
  }

  .image-link {
    display: inline-block;
  }

  .image-link::after {
    display: none;
  }

  img {
    display: inline-block;
    width: 8em;
    height: auto;
    border-radius: 50%;
    transform-origin: center;
    transition: transform 0.5s var(--easing-standard), opacity var(--color-transition);
  }

  .image-link:focus-visible img {
    transform: scale(1.05) rotate(15deg);
  }

  @media (hover: hover) {
    .image-link:hover img {
      transform: scale(1.05) rotate(15deg);
    }
  }
</style>
