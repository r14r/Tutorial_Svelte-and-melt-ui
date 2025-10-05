<script>
  import { createToggle } from '@melt-ui/svelte';

  const {
    elements: { root },
    states: { pressed }
  } = createToggle({ defaultPressed: true });
</script>

<h1>Toggle</h1>
<p class="lead">Switch a boolean state with accessible keyboard support.</p>

<button class="toggle" use:root>
  {#if $pressed}
    Notifications on
  {:else}
    Notifications off
  {/if}
</button>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .toggle {
    border: none;
    padding: 0.75rem 1.25rem;
    border-radius: 9999px;
    background: rgba(37, 99, 235, 0.15);
    color: #1d4ed8;
    font-weight: 600;
    cursor: pointer;
  }
</style>
