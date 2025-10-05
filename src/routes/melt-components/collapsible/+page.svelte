<script>
  import { createCollapsible } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { root, trigger, content }
  } = createCollapsible({ defaultOpen: true });
</script>

<h1>Collapsible</h1>
<p class="lead">Toggle sections of content with smooth height animations.</p>

<div class="collapsible" use:root>
  <button class="collapsible-trigger" use:trigger>Toggle details</button>
  <div class="collapsible-content" use:content>
    <p>
      Collapsibles provide a low-level primitive for toggling content visibility. Combine them with
      transitions or animation libraries for polished effects.
    </p>
  </div>
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .collapsible {
    display: grid;
    gap: 1rem;
    max-width: 420px;
  }

  .collapsible-trigger {
    border: none;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    background: #1d4ed8;
    color: white;
    font-weight: 600;
    cursor: pointer;
  }

  .collapsible-content {
    background: rgba(37, 99, 235, 0.08);
    border-radius: 0.75rem;
    padding: 1rem 1.25rem;
    line-height: 1.6;
  }
</style>
