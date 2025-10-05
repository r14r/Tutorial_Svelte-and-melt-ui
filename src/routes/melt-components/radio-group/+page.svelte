<script>
  import { createRadioGroup } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { root, item }
  } = createRadioGroup({ defaultValue: 'full' });

  const options = [
    { value: 'outline', label: 'Outline' },
    { value: 'ghost', label: 'Ghost' },
    { value: 'full', label: 'Solid' }
  ];
</script>

<h1>Radio Group</h1>
<p class="lead">Pick exactly one option from a related set.</p>

<div class="radio" use:root>
  {#each options as option}
    <label class="radio-option">
      <input class="sr-only" type="radio" use:item={{ value: option.value }} />
      <span class="radio-control" aria-hidden="true"></span>
      {option.label}
    </label>
  {/each}
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }

  .radio {
    display: flex;
    gap: 0.75rem;
  }

  .radio-option {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    border: none;
    background: rgba(15, 23, 42, 0.05);
    padding: 0.5rem 0.75rem;
    border-radius: 0.75rem;
    font: inherit;
    color: inherit;
    cursor: pointer;
    outline: none;
  }

  .radio-option:focus-visible {
    outline: 2px solid rgba(37, 99, 235, 0.6);
    outline-offset: 2px;
  }

  .radio-control {
    width: 1rem;
    height: 1rem;
    border-radius: 9999px;
    border: 2px solid rgba(37, 99, 235, 0.4);
  }

  :global(.radio-option[data-state='checked'] .radio-control) {
    background: #2563eb;
    border-color: #2563eb;
  }
</style>
