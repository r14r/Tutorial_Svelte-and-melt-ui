<script>
  import { createTabs } from '@melt-ui/svelte';

  const {
    elements: { root, list, trigger, content }
  } = createTabs({ defaultValue: 'overview' });

  const tabs = [
    {
      value: 'overview',
      label: 'Overview',
      copy: 'Overview content goes here.'
    },
    {
      value: 'api',
      label: 'API',
      copy: 'API reference content.'
    },
    {
      value: 'examples',
      label: 'Examples',
      copy: 'Example usage and recipes.'
    }
  ];
</script>

<h1>Tabs</h1>
<p class="lead">Switch between views without re-rendering the page.</p>

<div class="tabs" use:root>
  <div class="tab-list" use:list>
    {#each tabs as tab}
      <button class="tab-trigger" use:trigger={{ value: tab.value }}>{tab.label}</button>
    {/each}
  </div>
  {#each tabs as tab}
    <div class="tab-content" use:content={{ value: tab.value }}>
      <p>{tab.copy}</p>
    </div>
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

  .tabs {
    border: 1px solid rgba(15, 23, 42, 0.12);
    border-radius: 1rem;
    overflow: hidden;
  }

  .tab-list {
    display: flex;
    background: rgba(15, 23, 42, 0.05);
  }

  .tab-trigger {
    flex: 1;
    padding: 0.75rem 1rem;
    background: transparent;
    border: none;
    cursor: pointer;
    font-weight: 600;
  }

  .tab-content {
    padding: 1.5rem;
  }
</style>
