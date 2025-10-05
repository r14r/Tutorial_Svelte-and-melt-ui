<script>
  import { createAvatar } from '@melt-ui/svelte';

  const {
    elements: { root, image, fallback }
  } = createAvatar({
    src: 'https://i.pravatar.cc/150?img=5',
    delayMs: 0
  });
</script>

<h1>Avatar</h1>
<p class="lead">Shows a user image with automatic fallback initials.</p>

<div class="avatar" use:root>
  <img class="avatar-image" src="https://i.pravatar.cc/150?img=5" alt="Jules Doe" use:image />
  <span class="avatar-fallback" use:fallback>JD</span>
</div>

<style>
  h1 {
    margin: 0 0 0.5rem 0;
  }

  .lead {
    margin: 0 0 1.5rem 0;
    color: rgba(15, 23, 42, 0.7);
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
</style>
