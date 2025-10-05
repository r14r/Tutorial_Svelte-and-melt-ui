<script>
  import { createTooltip } from '@melt-ui/svelte';

  const {
    elements: { trigger, content, arrow }
  } = createTooltip({
    positioning: { placement: 'top' },
    openDelay: 0,
    closeDelay: 0,
    closeOnPointerDown: false,
    forceVisible: true
  });
</script>

<h1>Tooltip</h1>
<p class="lead">Add helpful hints without cluttering the interface.</p>

<button class="tooltip-trigger" use:trigger>Hover me</button>
<div class="tooltip-content" use:content>
  <div class="tooltip-arrow" use:arrow></div>
  Quick tip via Melt UI tooltip.
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .tooltip-trigger {
    position: relative;
    border: none;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    background: rgba(37, 99, 235, 0.15);
    color: #1d4ed8;
    cursor: pointer;
  }

  .tooltip-content {
    position: absolute;
    bottom: calc(100% + 0.5rem);
    left: 50%;
    transform: translateX(-50%);
    padding: 0.5rem 0.75rem;
    border-radius: 0.5rem;
    background: #1d4ed8;
    color: white;
    font-size: 0.85rem;
    white-space: nowrap;
  }

  .tooltip-arrow {
    position: absolute;
    top: 100%;
    left: 50%;
    width: 0.75rem;
    height: 0.75rem;
    background: #1d4ed8;
    transform: translate(-50%, -50%) rotate(45deg);
  }
</style>
