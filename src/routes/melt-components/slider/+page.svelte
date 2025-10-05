<script>
  import { createSlider } from '@melt-ui/svelte';

  export let params;
  $: void params;

  const {
    elements: { root, range, thumb },
    states: { value }
  } = createSlider({
    min: 0,
    max: 100,
    step: 1,
    defaultValue: [30]
  });
</script>

<h1>Slider</h1>
<p class="lead">Pick a numeric value with pointer, touch, or keyboard input.</p>

<div class="slider" use:root>
  <div class="slider-track">
    <div class="slider-range" use:range></div>
  </div>
  <div class="slider-thumb" use:thumb></div>
</div>
<p class="value">Current value: {$value[0]}</p>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
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

  .value {
    color: rgba(15, 23, 42, 0.6);
  }
</style>
