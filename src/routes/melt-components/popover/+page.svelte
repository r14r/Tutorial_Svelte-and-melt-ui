<script>
  import { createPopover } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { trigger, content }
  } = createPopover();
</script>

<h1>Popover</h1>
<p class="lead">Layer floating content that responds to pointer and keyboard interactions.</p>

<button class="popover-trigger" use:trigger>View shortcuts</button>
<div class="popover-content" use:content>
  <p><strong>⌘K</strong> — Command palette</p>
  <p><strong>⌘P</strong> — Open file</p>
  <p><strong>⇧⌘F</strong> — Search in files</p>
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .popover-trigger {
    border: none;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    background: #1d4ed8;
    color: white;
    cursor: pointer;
  }

  .popover-content {
    margin-top: 0.75rem;
    border-radius: 0.75rem;
    border: 1px solid rgba(15, 23, 42, 0.12);
    padding: 1rem;
    background: white;
    max-width: 280px;
    box-shadow: 0 15px 35px -30px rgba(15, 23, 42, 0.7);
  }
</style>
