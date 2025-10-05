<script>
  import { componentPages } from './components';

  export let params;
  $: void params;

  const componentLinks = componentPages.filter((item) => item.slug !== '');
</script>

<h1>Welcome to the Melt UI component gallery</h1>
<p class="lead">
  Explore the collection of interactive primitives used throughout this tutorial. Each page focuses on
  a single component so you can study the API, markup, and styles in isolation.
</p>

<div class="grid">
  {#each componentLinks as item}
    <a class="card" href={item.slug ? `/melt-components/${item.slug}` : '/melt-components'}>
      <span class="card-label">{item.label}</span>
      <span class="card-action">View demo →</span>
    </a>
  {/each}
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 2rem 0;
    color: rgba(15, 23, 42, 0.7);
    max-width: 50ch;
  }

  .grid {
    display: grid;
    gap: 1rem;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  }

  .card {
    display: flex;
    flex-direction: column;
    gap: 0.35rem;
    padding: 1.25rem;
    border-radius: 1.25rem;
    text-decoration: none;
    color: inherit;
    border: 1px solid rgba(15, 23, 42, 0.1);
    background: rgba(255, 255, 255, 0.9);
    box-shadow: 0 18px 45px -40px rgba(15, 23, 42, 0.8);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .card:hover,
  .card:focus-visible {
    transform: translateY(-2px);
    box-shadow: 0 30px 65px -50px rgba(37, 99, 235, 0.75);
    outline: none;
  }

  .card-label {
    font-weight: 600;
  }

  .card-action {
    font-size: 0.9rem;
    color: rgba(37, 99, 235, 0.8);
  }
</style>
