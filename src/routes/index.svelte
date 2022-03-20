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
    Fluent in both design & code<br />
    Prefers work to speak for itself<br />
    <a rel="external" target="_blank" href="mailto:the.nick.vincent@gmail.com"
      >the.nick.vincent@gmail.com</a
    >
  </p>
</PageTransition>

<style>
  h1,
  p {
    margin: 0;
    text-align: center;
  }

  .image-link {
    display: block;
    width: fit-content;
    margin: 0 auto;
    border-radius: 50%;
    border: 0.1em solid var(--color-line);
    transition: transform 1s var(--easing-standard), var(--dom-x-ray-transition);
  }

  .image-link::after {
    display: none;
  }

  img {
    display: block;
    width: 8em;
    height: auto;
    border-radius: 50%;
  }

  .image-link:focus-visible {
    transform: scale(1.05) rotate(15deg);
  }

  @media (hover: hover) {
    .image-link:hover {
      transform: scale(1.05) rotate(15deg);
    }
  }
</style>
