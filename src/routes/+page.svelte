<script>
  export let params;
  $: void params;

</script>

<section class="hero">
  <h1>Welcome to the Svelte + Melt UI tutorial project</h1>
  <p>
    This mini app shows how you can wire up <strong>Melt UI</strong> primitives inside a modern
    SvelteKit project. Explore the curated playground of components to see how to compose
    accessible interactions with only a handful of lines of Svelte code.
  </p>
  <a class="cta" href="/melt-components">Browse the component gallery</a>
</section>

<section class="content">
  <div class="card">
    <h2>What is Melt UI?</h2>
    <p>
      Melt UI provides unstyled, accessible primitives that allow you to build interactive
      experiences without sacrificing design freedom. Pair it with your own styles or favourite CSS
      framework to craft bespoke interfaces.
    </p>
  </div>
  <div class="card">
    <h2>How this demo is structured</h2>
    <p>
      Each section in the gallery focuses on one Melt UI primitive with a concise example and
      short explanation. Use it as a reference or starting point for your own projects.
    </p>
  </div>
</section>

<style>
  .hero {
    display: grid;
    gap: 1.5rem;
    padding: 3rem;
    border-radius: 1.75rem;
    background: linear-gradient(135deg, rgba(59, 130, 246, 0.15), rgba(59, 130, 246, 0));
    box-shadow: 0 25px 60px -40px rgba(15, 23, 42, 0.8);
  }

  h1 {
    font-size: clamp(2rem, 5vw, 3.25rem);
    margin: 0;
  }

  p {
    font-size: 1.05rem;
    line-height: 1.7;
    margin: 0;
    color: rgba(15, 23, 42, 0.8);
  }

  .cta {
    align-self: start;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 0.85rem 1.6rem;
    border-radius: 9999px;
    background: #1d4ed8;
    color: white;
    font-weight: 600;
    letter-spacing: 0.02em;
    text-decoration: none;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .cta:hover,
  .cta:focus {
    transform: translateY(-1px);
    box-shadow: 0 16px 40px -20px rgba(37, 99, 235, 0.7);
  }

  .content {
    margin-top: 2.5rem;
    display: grid;
    gap: 1.5rem;
  }

  .card {
    padding: 2rem;
    border-radius: 1.5rem;
    border: 1px solid rgba(15, 23, 42, 0.1);
    background: rgba(255, 255, 255, 0.85);
    backdrop-filter: blur(8px);
    box-shadow: 0 15px 40px -35px rgba(15, 23, 42, 0.9);
  }

  .card h2 {
    margin: 0 0 0.75rem 0;
  }
</style>
