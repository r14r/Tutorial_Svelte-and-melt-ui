<script>
  import { createAccordion } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { root, item, trigger, content }
  } = createAccordion({
    defaultValue: 'intro'
  });

  const items = [
    {
      value: 'intro',
      title: 'Getting started',
      body: 'Install Melt UI and import the primitives you need.'
    },
    {
      value: 'theming',
      title: 'Style freely',
      body: 'Melt UI ships unstyled, accessible primitives so you can use any design system.'
    },
    {
      value: 'interop',
      title: 'Composable',
      body: 'Compose primitives together to build complex experiences without sacrificing ergonomics.'
    }
  ];
</script>

<h1>Accordion</h1>
<p class="lead">Stack collapsible sections that manage focus and keyboard interactions automatically.</p>

<div class="accordion" use:root>
  {#each items as accordionItem (accordionItem.value)}
    <div class="accordion-item" use:item={{ value: accordionItem.value }}>
      <button class="accordion-trigger" use:trigger={{ value: accordionItem.value }}>
        {accordionItem.title}
      </button>
      <div class="accordion-content" use:content={{ value: accordionItem.value }}>
        <p>{accordionItem.body}</p>
      </div>
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

  .accordion {
    border-radius: 1rem;
    border: 1px solid rgba(15, 23, 42, 0.08);
    overflow: hidden;
  }

  .accordion-item + .accordion-item {
    border-top: 1px solid rgba(15, 23, 42, 0.08);
  }

  .accordion-trigger {
    width: 100%;
    text-align: left;
    padding: 1rem 1.25rem;
    font-weight: 600;
    background: transparent;
    border: none;
    cursor: pointer;
  }

  .accordion-content {
    padding: 0 1.25rem 1rem;
    line-height: 1.6;
  }
</style>
