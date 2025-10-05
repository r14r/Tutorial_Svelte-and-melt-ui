<script>
  import { onMount } from 'svelte';
  import { createToaster } from '@melt-ui/svelte';

  const {
    elements: { content, title, description, close },
    helpers: { addToast },
    states: { toasts },
    actions: { portal }
  } = createToaster();

  onMount(() => {
    const timer = setTimeout(() => {
      addToast({
        data: {
          title: 'Welcome!',
          description: 'Try interacting with the Melt UI toaster below.'
        }
      });
    }, 800);

    return () => clearTimeout(timer);
  });
</script>

<h1>Toaster</h1>
<p class="lead">Trigger transient notifications with predictable focus management.</p>

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
  {#each $toasts as toast (toast.id)}
    <div class="toast" use:content={toast}>
      <div>
        <strong use:title={toast}>{toast.data.title}</strong>
        <p use:description={toast}>{toast.data.description}</p>
      </div>
      <button class="toast-close" use:close={toast}>×</button>
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
</style>
