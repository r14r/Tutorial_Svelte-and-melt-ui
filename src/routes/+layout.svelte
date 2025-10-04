<svelte:head>
  <title>Tutorial - Svelte & Melt UI</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<nav class="navbar">
  <div class="logo">Svelte × Melt UI</div>
  <div class="links">
    <a href="/">Home</a>
    <a href="/melt-components">Melt Components</a>
  </div>
</nav>

<main>
  <slot />
</main>

<style>
  :global(body) {
    margin: 0;
    font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    background: radial-gradient(circle at top, #f3f4ff 0%, #f8fafc 60%, #ffffff 100%);
    color: #0f172a;
    min-height: 100vh;
  }

  :global(a) {
    color: inherit;
  }

  .navbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem 2rem;
    border-bottom: 1px solid rgba(15, 23, 42, 0.08);
    backdrop-filter: blur(12px);
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(248, 250, 252, 0.75);
  }

  .logo {
    font-weight: 700;
    font-size: 1.1rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .links {
    display: flex;
    gap: 1rem;
  }

  .links a {
    text-decoration: none;
    font-weight: 500;
    padding: 0.5rem 0.75rem;
    border-radius: 0.75rem;
    transition: background 0.2s ease, color 0.2s ease;
  }

  .links a:hover,
  .links a:focus {
    background: rgba(59, 130, 246, 0.12);
    color: #1d4ed8;
  }

  main {
    padding: 2rem clamp(1rem, 4vw, 3rem);
    max-width: 1100px;
    margin: 0 auto;
  }
</style>
