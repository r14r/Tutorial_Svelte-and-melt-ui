<script>
  import { createPinInput } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { root, input }
  } = createPinInput({
    name: 'pin',
    placeholder: '•'
  });
</script>

<h1>PIN Input</h1>
<p class="lead">Capture secure numeric codes with managed focus flow.</p>

<div class="pin" use:root>
  {#each Array(4) as _, i}
    <input class="pin-input" inputmode="numeric" autocomplete="one-time-code" maxlength="1" use:input />
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
</style>
