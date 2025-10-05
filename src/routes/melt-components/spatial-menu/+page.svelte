<script>
  const actions = [
    { id: 'new', label: 'New File', description: 'Create a document' },
    { id: 'open', label: 'Open…', description: 'Browse recent files' },
    { id: 'share', label: 'Share', description: 'Invite collaborators' }
  ];
</script>

<h1>Spatial Menu (WIP)</h1>
<p class="lead">
  Navigate menu items by pointing in the direction of a radial layout—perfect for power tools and creative
  applications.
</p>

<div class="spatial-menu">
  {#each actions as action}
    <button>
      <strong>{action.label}</strong>
      <span>{action.description}</span>
    </button>
  {/each}
</div>
<p class="note">
  Melt UI's spatial menu is currently work in progress, so this demo uses simplified markup to illustrate the
  concept.
</p>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
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
</style>
