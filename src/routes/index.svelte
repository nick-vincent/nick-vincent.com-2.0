<script>
  import PageTransition from './_page_transition.svelte';
</script>

<svelte:head>
  <title>Nick Vincent: Fluent in design and code</title>
</svelte:head>

<PageTransition>
  <img alt="Nick Vincent" src="/nick-vincent.jpg" width="640" height="640" />
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
    display: block;
    width: calc(50% - 0.5em);
    height: auto;
    margin-bottom: 0.5em;
    border-radius: 50%;
  }
</style>
