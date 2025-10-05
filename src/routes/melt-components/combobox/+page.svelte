<script>
  import { createCombobox } from '@melt-ui/svelte';

  const {
    elements: { input, menu, option }
  } = createCombobox({
    forceVisible: true
  });

  const options = ['Accordion', 'Avatar', 'Combobox', 'Slider', 'Tabs'];
</script>

<h1>Combobox</h1>
<p class="lead">Autocomplete an item from a list with keyboard-friendly navigation.</p>

<div class="combobox">
  <input class="combobox-input" placeholder="Search components…" use:input />
  <div class="combobox-menu" use:menu>
    {#each options as label}
      <div class="combobox-item" use:option={{ value: label, label }}>{label}</div>
    {/each}
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

  .combobox {
    position: relative;
    max-width: 320px;
  }

  .combobox-input {
    width: 100%;
    padding: 0.75rem 1rem;
    border-radius: 0.75rem;
    border: 1px solid rgba(15, 23, 42, 0.12);
  }

  .combobox-menu {
    margin-top: 0.5rem;
    border-radius: 0.75rem;
    border: 1px solid rgba(15, 23, 42, 0.12);
    background: white;
    box-shadow: 0 15px 35px -30px rgba(15, 23, 42, 0.7);
  }

  .combobox-item {
    padding: 0.65rem 1rem;
    cursor: pointer;
  }

  .combobox-item:hover {
    background: rgba(37, 99, 235, 0.1);
  }
</style>
