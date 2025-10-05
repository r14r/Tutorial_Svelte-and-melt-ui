<script>
  import { createTooltip } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { trigger, content, arrow }
  } = createTooltip({
    positioning: { placement: 'top' },
    openDelay: 150,
    closeDelay: 100
  });
</script>

<h1>Tooltip</h1>
<p class="lead">Add helpful hints without cluttering the interface.</p>

<div class="tooltip">
  <button class="tooltip-trigger" use:trigger>Hover me</button>
  <div class="tooltip-content" use:content>
    <div class="tooltip-arrow" use:arrow></div>
    Quick tip via Melt UI tooltip.
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

  .tooltip {
    display: inline-flex;
    position: relative;
  }

  .tooltip-trigger {
    border: none;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    background: rgba(37, 99, 235, 0.15);
    color: #1d4ed8;
    cursor: pointer;
  }

  .tooltip-content {
    z-index: 20;
    pointer-events: none;
    padding: 0.5rem 0.75rem;
    border-radius: 0.5rem;
    background: #1d4ed8;
    color: white;
    font-size: 0.85rem;
    white-space: nowrap;
    box-shadow: 0 10px 25px -20px rgba(15, 23, 42, 0.6);
    transition: opacity 0.15s ease, transform 0.15s ease;
  }

  .tooltip-content[data-state='closed'] {
    opacity: 0;
    transform: scale(0.96);
  }

  .tooltip-content[data-state='open'] {
    opacity: 1;
    transform: scale(1);
    pointer-events: auto;
  }

  .tooltip-content[data-side='top'] {
    transform-origin: bottom center;
  }

  .tooltip-content[data-side='bottom'] {
    transform-origin: top center;
  }

  .tooltip-content[data-side='left'] {
    transform-origin: center right;
  }

  .tooltip-content[data-side='right'] {
    transform-origin: center left;
  }

  .tooltip-arrow {
    width: 0.6rem;
    height: 0.6rem;
    background: #1d4ed8;
    transform: rotate(45deg);
  }
</style>
