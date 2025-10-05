<script>
  import { onMount } from 'svelte';
  import {
    createAccordion,
    createAvatar,
    createCollapsible,
    createCombobox,
    createPinInput,
    createPopover,
    createProgress,
    createRadioGroup,
    createSelect,
    createSlider,
    createTabs,
    createToaster,
    createToggle,
    createTooltip
  } from '@melt-ui/svelte';

  // Accordion - destructure elements correctly
  const {
    elements: { root: accordionRoot, item, trigger, content },
    helpers: { isSelected }
  } = createAccordion({
    defaultValue: 'intro'
  });

  const accordionItems = [
    { value: 'intro', title: 'Getting started', body: 'Install Melt UI and import the primitives you need.' },
    { value: 'theming', title: 'Style freely', body: 'Melt UI ships unstyled, accessible primitives so you can use any design system.' },
    { value: 'interop', title: 'Composable', body: 'Compose primitives together to build complex experiences without sacrificing ergonomics.' }
  ];

  // Avatar
  const {
    elements: { root: avatarRoot, image: avatarImage, fallback: avatarFallback }
  } = createAvatar({
    src: 'https://i.pravatar.cc/150?img=5',
    delayMs: 0
  });

  // Collapsible
  const {
    elements: { root: collapsibleRoot, trigger: collapsibleTrigger, content: collapsibleContent }
  } = createCollapsible({ defaultOpen: true });

  // Combobox
  const {
    elements: { input: comboInput, menu: comboMenu, option: comboOption }
  } = createCombobox({
    forceVisible: true
  });
  const comboItems = ['Accordion', 'Avatar', 'Combobox', 'Slider', 'Tabs'];

  // PIN Input
  const {
    elements: { root: pinRoot, input: pinInput }
  } = createPinInput({
    name: 'pin',
    placeholder: '•'
  });

  // Popover
  const {
    elements: { trigger: popoverTrigger, content: popoverContent }
  } = createPopover();

  // Progress
  const {
    elements: { root: progressRoot }
  } = createProgress({ value: 45, max: 100 });

  // Radio Group
  const {
    elements: { root: radioRoot, item: radioItem }
  } = createRadioGroup({ defaultValue: 'full' });
  const radioOptions = [
    { value: 'outline', label: 'Outline' },
    { value: 'ghost', label: 'Ghost' },
    { value: 'full', label: 'Solid' }
  ];

  // Select
  const {
    elements: { trigger: selectTrigger, menu: selectMenu, option: selectOption, label: selectLabel },
    states: { selectedLabel, open: selectOpen }
  } = createSelect({
    forceVisible: true,
    positioning: {
      placement: 'bottom',
      fitViewport: true,
      sameWidth: true
    }
  });
  const selectOptions = [
    { value: 'svelte', label: 'Svelte' },
    { value: 'melt', label: 'Melt UI' },
    { value: 'tailwind', label: 'Tailwind' }
  ];

  // Slider
  const {
    elements: { root: sliderRoot, range: sliderRange, thumb: sliderThumb },
    states: { value: sliderValue }
  } = createSlider({
    min: 0,
    max: 100,
    step: 1,
    defaultValue: [30]
  });

  // Tabs
  const {
    elements: { root: tabsRoot, list: tabsList, trigger: tabsTrigger, content: tabsContent }
  } = createTabs({ defaultValue: 'overview' });
  const tabsData = [
    { value: 'overview', label: 'Overview' },
    { value: 'api', label: 'API' },
    { value: 'examples', label: 'Examples' }
  ];

  // Toaster
  const {
    elements: { content: toastContent, title: toastTitle, description: toastDescription, close: toastClose },
    helpers: { addToast },
    states: { toasts },
    actions: { portal }
  } = createToaster();

  // Toggle
  const {
    elements: { root: toggleRoot },
    states: { pressed }
  } = createToggle({ defaultPressed: true });

  // Tooltip
  const {
    elements: { trigger: tooltipTrigger, content: tooltipContent, arrow: tooltipArrow }
  } = createTooltip({ positioning: { placement: 'top' }, openDelay: 0, closeDelay: 0, closeOnPointerDown: false, forceVisible: true });

  const spatialMenuItems = [
    { id: 'new', label: 'New File', description: 'Create a document' },
    { id: 'open', label: 'Open…', description: 'Browse recent files' },
    { id: 'share', label: 'Share', description: 'Invite collaborators' }
  ];

  onMount(() => {
    const timer = setTimeout(() => {
      addToast({
        data: {
          title: 'Welcome!',
          description: 'Try interacting with the Melt UI primitives below.'
        }
      });
    }, 800);

    return () => clearTimeout(timer);
  });
</script>

<h1>Melt UI component gallery</h1>
<p class="lead">
  Each example below is intentionally minimal so you can focus on the Melt UI primitive itself. The
  styles are handcrafted for this demo, but the interaction logic is provided entirely by Melt UI.
</p>

<section class="component">
  <header>
    <h2>Accordion</h2>
    <p>Stack collapsible sections that manage focus and keyboard interactions automatically.</p>
  </header>
  <div class="accordion" use:accordionRoot>
    {#each accordionItems as accordionItem (accordionItem.value)}
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
</section>

<section class="component">
  <header>
    <h2>Avatar</h2>
    <p>Shows a user image with automatic fallback initials.</p>
  </header>
  <div class="avatar" use:avatarRoot>
    <img class="avatar-image" src="https://i.pravatar.cc/150?img=5" alt="Jules Doe" use:avatarImage />
    <span class="avatar-fallback" use:avatarFallback>JD</span>
  </div>
</section>

<section class="component">
  <header>
    <h2>Collapsible</h2>
    <p>Toggle sections of content with smooth height animations.</p>
  </header>
  <div class="collapsible" use:collapsibleRoot>
    <button class="collapsible-trigger" use:collapsibleTrigger>Toggle details</button>
    <div class="collapsible-content" use:collapsibleContent>
      <p>
        Collapsibles provide a low-level primitive for toggling content visibility. Combine them with
        transitions or animation libraries for polished effects.
      </p>
    </div>
  </div>
</section>

<section class="component">
  <header>
    <h2>Combobox</h2>
    <p>Autocomplete an item from a list with keyboard-friendly navigation.</p>
  </header>
  <div class="combobox">
    <input class="combobox-input" placeholder="Search components…" use:comboInput />
    <div class="combobox-menu" use:comboMenu>
      {#each comboItems as option}
        <div class="combobox-item" use:comboOption={{ value: option, label: option }}>{option}</div>
      {/each}
    </div>
  </div>
</section>

<section class="component">
  <header>
    <h2>PIN Input</h2>
    <p>Capture secure numeric codes with managed focus flow.</p>
  </header>
  <div class="pin" use:pinRoot>
    {#each Array(4) as _, i}
      <input class="pin-input" use:pinInput />
    {/each}
  </div>
</section>

<section class="component">
  <header>
    <h2>Popover</h2>
    <p>Layer floating content that responds to pointer and keyboard interactions.</p>
  </header>
  <button class="popover-trigger" use:popoverTrigger>View shortcuts</button>
  <div class="popover-content" use:popoverContent>
    <p><strong>⌘K</strong> — Command palette</p>
    <p><strong>⌘P</strong> — Open file</p>
    <p><strong>⇧⌘F</strong> — Search in files</p>
  </div>
</section>

<section class="component">
  <header>
    <h2>Progress</h2>
    <p>Display task completion using an accessible progress element.</p>
  </header>
  <div class="progress" use:progressRoot>
    <div class="progress-bar" style="width: 45%"></div>
  </div>
</section>

<section class="component">
  <header>
    <h2>Radio Group</h2>
    <p>Pick exactly one option from a related set.</p>
  </header>
  <div class="radio" use:radioRoot>
    {#each radioOptions as option}
      <label class="radio-option">
        <input class="sr-only" type="radio" use:radioItem={{ value: option.value }} />
        <span class="radio-control" aria-hidden="true"></span>
        {option.label}
      </label>
    {/each}
  </div>
</section>

<section class="component">
  <header>
    <h2>Select</h2>
    <p>Compose a fully accessible select menu with custom styling.</p>
  </header>
  <div class="select">
    <button class="select-trigger" use:selectTrigger>
      <span>{$selectedLabel || 'Choose a stack'}</span>
      <span class="caret">▾</span>
    </button>
    {#if $selectOpen}
      <div class="select-content" use:selectMenu>
        {#each selectOptions as option}
          <div class="select-item" use:selectOption={{ value: option.value, label: option.label }}>
            {option.label}
          </div>
        {/each}
      </div>
    {/if}
  </div>
</section>

<section class="component">
  <header>
    <h2>Slider</h2>
    <p>Pick a numeric value with pointer, touch, or keyboard input.</p>
  </header>
  <div class="slider" use:sliderRoot>
    <div class="slider-track">
      <div class="slider-range" use:sliderRange></div>
    </div>
    <div class="slider-thumb" use:sliderThumb></div>
  </div>
</section>

<section class="component">
  <header>
    <h2>Spatial Menu (WIP)</h2>
    <p>
      Navigate menu items by pointing in the direction of a radial layout—perfect for power tools
      and creative applications.
    </p>
  </header>
  <div class="spatial-menu">
    {#each spatialMenuItems as action}
      <button>
        <strong>{action.label}</strong>
        <span>{action.description}</span>
      </button>
    {/each}
  </div>
  <p class="note">
    Melt UI's spatial menu is currently work in progress, so this demo uses simplified markup to
    illustrate the concept.
  </p>
</section>

<section class="component">
  <header>
    <h2>Tabs</h2>
    <p>Switch between views without re-rendering the page.</p>
  </header>
  <div class="tabs" use:tabsRoot>
    <div class="tab-list" use:tabsList>
      {#each tabsData as tab}
        <button class="tab-trigger" use:tabsTrigger={{ value: tab.value }}>{tab.label}</button>
      {/each}
    </div>
    <div class="tab-content" use:tabsContent ={{ value: 'overview' }}>
      <p>Overview content goes here.</p>
    </div>
    <div class="tab-content" use:tabsContent ={{ value: 'api' }}>
      <p>API reference content.</p>
    </div>
    <div class="tab-content" use:tabsContent ={{ value: 'examples' }}>
      <p>Example usage and recipes.</p>
    </div>
  </div>
</section>

<section class="component">
  <header>
    <h2>Toaster</h2>
    <p>Trigger transient notifications with predictable focus management.</p>
  </header>
  <button
    class="toast-button"
    on:click={() =>
      addToast({
        data: {
          title: 'Saved!',
          description: 'Your preferences have been updated.'
        }
      })}
  >
    Show toast
  </button>
  <div class="toaster" use:portal>
    {#each $toasts as t (t.id)}
      <div class="toast" use:toastContent={t}>
        <div>
          <strong use:toastTitle={t}>{t.data.title}</strong>
          <p use:toastDescription={t}>{t.data.description}</p>
        </div>
        <button class="toast-close" use:toastClose={t}>×</button>
      </div>
    {/each}
  </div>
</section>

<section class="component">
  <header>
    <h2>Toggle</h2>
    <p>Switch a boolean state with accessible keyboard support.</p>
  </header>
  <button class="toggle" use:toggleRoot>
    {#if $pressed}
      Notifications on
    {:else}
      Notifications off
    {/if}
  </button>
</section>

<section class="component">
  <header>
    <h2>Tooltip</h2>
    <p>Add helpful hints without cluttering the interface.</p>
  </header>
  <button class="tooltip-trigger" use:tooltipTrigger>
    Hover me
  </button>
  <div class="tooltip-content" use:tooltipContent>
    <div use:tooltipArrow />
    Quick tip via Melt UI tooltip.
  </div>
</section>

<style>
  h1 {
    margin-bottom: 0.25rem;
  }

  .lead {
    margin-top: 0;
    margin-bottom: 2rem;
    color: rgba(15, 23, 42, 0.75);
  }

  .component {
    margin-bottom: 3rem;
    padding-bottom: 2.5rem;
    border-bottom: 1px solid rgba(15, 23, 42, 0.08);
  }

  .component header {
    margin-bottom: 1.5rem;
  }

  .component h2 {
    margin: 0 0 0.25rem 0;
  }

  .component p {
    margin: 0;
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

  .avatar {
    width: 80px;
    height: 80px;
    border-radius: 9999px;
    position: relative;
    overflow: hidden;
    display: grid;
    place-items: center;
    background: rgba(37, 99, 235, 0.1);
    color: #1d4ed8;
    font-weight: 600;
    font-size: 1.5rem;
  }

  .avatar-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
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
    margin-top: 1rem;
    background: rgba(37, 99, 235, 0.08);
    border-radius: 0.75rem;
    padding: 1rem 1.25rem;
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

  .pin {
    display: flex;
    gap: 0.75rem;
  }

  .pin-input {
    width: 3rem;
    height: 3rem;
    text-align: center;
    border-radius: 0.75rem;
    border: 1px solid rgba(15, 23, 42, 0.15);
    font-size: 1.25rem;
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

  .slider {
    width: 100%;
    max-width: 420px;
    position: relative;
  }

  .slider-track {
    height: 0.35rem;
    border-radius: 9999px;
    background: rgba(15, 23, 42, 0.12);
  }

  .slider-range {
    height: 100%;
    background: linear-gradient(135deg, #2563eb, #22d3ee);
  }

  .slider-thumb {
    width: 1.25rem;
    height: 1.25rem;
    border-radius: 9999px;
    background: white;
    border: 2px solid #2563eb;
    position: absolute;
    top: -0.45rem;
  }

  .spatial-menu {
    display: flex;
    gap: 0.75rem;
    flex-wrap: wrap;
  }

  .spatial-menu button {
    flex: 1 1 160px;
    padding: 0.85rem;
    border-radius: 1rem;
    border: 1px solid rgba(15, 23, 42, 0.12);
    background: rgba(37, 99, 235, 0.05);
    cursor: pointer;
    text-align: left;
  }

  .note {
    margin-top: 0.75rem;
    font-size: 0.875rem;
    color: rgba(15, 23, 42, 0.6);
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

  .toast-button {
    border: none;
    padding: 0.75rem 1.25rem;
    border-radius: 0.75rem;
    background: #1d4ed8;
    color: white;
    cursor: pointer;
  }

  .toaster {
    margin-top: 1rem;
    display: grid;
    gap: 0.75rem;
    max-width: 380px;
  }

  .toast {
    border-radius: 0.75rem;
    background: white;
    border: 1px solid rgba(15, 23, 42, 0.12);
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
  }

  .toast-close {
    border: none;
    background: rgba(15, 23, 42, 0.06);
    border-radius: 9999px;
    width: 2rem;
    height: 2rem;
    cursor: pointer;
  }

  .toggle {
    border: none;
    padding: 0.75rem 1.25rem;
    border-radius: 9999px;
    background: rgba(37, 99, 235, 0.15);
    color: #1d4ed8;
    font-weight: 600;
    cursor: pointer;
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
</style>
