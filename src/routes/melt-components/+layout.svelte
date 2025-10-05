<script>
  import { page } from '$app/stores';
  import { componentPages } from './components';

  export let params;
  $: void params;

  const linkFor = (slug) => (slug ? `/melt-components/${slug}` : '/melt-components');
</script>

<div class="gallery-layout">
  <aside class="sidebar">
    <h2>Component pages</h2>
    <nav>
      {#each componentPages as item}
        {#if item.slug === ''}
          <a
            href="/melt-components"
            class:active={$page.url.pathname === '/melt-components'}
            aria-current={$page.url.pathname === '/melt-components' ? 'page' : undefined}
          >
            {item.label}
          </a>
        {:else}
          <a
            href={linkFor(item.slug)}
            class:active={$page.url.pathname.startsWith(linkFor(item.slug))}
            aria-current={$page.url.pathname.startsWith(linkFor(item.slug)) ? 'page' : undefined}
          >
            {item.label}
          </a>
        {/if}
      {/each}
    </nav>
  </aside>
  <section class="content">
    <slot />
  </section>
</div>

<style>
  .gallery-layout {
    display: grid;
    grid-template-columns: minmax(220px, 260px) 1fr;
    gap: 2rem;
  }

  .sidebar {
    position: sticky;
    top: 6rem;
    align-self: start;
    padding: 1.5rem;
    border-radius: 1.25rem;
    border: 1px solid rgba(15, 23, 42, 0.08);
    background: rgba(255, 255, 255, 0.85);
    box-shadow: 0 18px 45px -40px rgba(15, 23, 42, 0.65);
    backdrop-filter: blur(12px);
  }

  .sidebar h2 {
    margin: 0 0 1rem 0;
    font-size: 1rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: rgba(15, 23, 42, 0.6);
  }

  nav {
    display: grid;
    gap: 0.35rem;
  }

  nav a {
    text-decoration: none;
    padding: 0.6rem 0.75rem;
    border-radius: 0.75rem;
    font-weight: 500;
    color: rgba(15, 23, 42, 0.75);
    transition: background 0.2s ease, color 0.2s ease;
  }

  nav a:hover,
  nav a:focus-visible {
    background: rgba(59, 130, 246, 0.12);
    color: #1d4ed8;
    outline: none;
  }

  nav a.active {
    background: #1d4ed8;
    color: white;
  }

  .content {
    padding: 1rem 1.5rem;
    border-radius: 1.5rem;
    background: rgba(255, 255, 255, 0.7);
    border: 1px solid rgba(15, 23, 42, 0.05);
    box-shadow: 0 25px 60px -45px rgba(15, 23, 42, 0.65);
    backdrop-filter: blur(8px);
  }

  @media (max-width: 900px) {
    .gallery-layout {
      grid-template-columns: 1fr;
    }

    .sidebar {
      position: static;
    }
  }
</style>
