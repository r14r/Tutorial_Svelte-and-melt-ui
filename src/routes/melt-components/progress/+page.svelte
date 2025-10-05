<script>
  import { createProgress } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { root }
  } = createProgress({ value: 45, max: 100 });
</script>

<h1>Progress</h1>
<p class="lead">Display task completion using an accessible progress element.</p>

<div class="progress" use:root>
  <div class="progress-bar" style="width: 45%"></div>
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .progress {
    height: 0.75rem;
    border-radius: 9999px;
    background: rgba(37, 99, 235, 0.12);
    overflow: hidden;
    max-width: 360px;
  }

  .progress-bar {
    height: 100%;
    background: linear-gradient(135deg, #2563eb, #22d3ee);
  }
</style>
