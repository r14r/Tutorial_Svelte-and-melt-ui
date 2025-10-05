<script>
  import { createSelect } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { trigger, menu, option },
    states: { selectedLabel, open }
  } = createSelect({
    forceVisible: true,
    positioning: {
      placement: 'bottom',
      fitViewport: true,
      sameWidth: true
    }
  });

  const options = [
    { value: 'svelte', label: 'Svelte' },
    { value: 'melt', label: 'Melt UI' },
    { value: 'tailwind', label: 'Tailwind' }
  ];
</script>

<h1>Select</h1>
<p class="lead">Compose a fully accessible select menu with custom styling.</p>

<div class="select">
  <button class="select-trigger" use:trigger>
    <span>{$selectedLabel || 'Choose a stack'}</span>
    <span class="caret">▾</span>
  </button>
  {#if $open}
    <div class="select-content" use:menu>
      {#each options as item}
        <div class="select-item" use:option={{ value: item.value, label: item.label }}>
          {item.label}
        </div>
      {/each}
    </div>
  {/if}
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
  }

  .select {
    position: relative;
    max-width: 260px;
  }

  .select-trigger {
    width: 100%;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    border: 1px solid rgba(15, 23, 42, 0.12);
    background: white;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .select-content {
    margin-top: 0.5rem;
    border-radius: 0.75rem;
    border: 1px solid rgba(15, 23, 42, 0.12);
    background: white;
    box-shadow: 0 15px 35px -30px rgba(15, 23, 42, 0.7);
  }

  .select-item {
    padding: 0.65rem 1rem;
    cursor: pointer;
  }

  .caret {
    font-size: 0.9rem;
    color: rgba(15, 23, 42, 0.6);
  }
</style>
