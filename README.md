# Tutorial – Svelte & Melt UI

This repository contains a minimal SvelteKit project that showcases how to wire up multiple
[Melt UI](https://github.com/melt-ui/melt-ui) primitives inside a single application. The codebase
targets **Svelte 5** together with the latest Melt UI builders so the examples mirror the current
APIs. The home page introduces the stack and the `/melt-components` route renders a gallery with
working examples of the following Melt UI components:

- Accordion
- Avatar
- Collapsible
- Combobox
- File Upload
- PIN Input
- Popover
- Progress
- Radio Group
- Select
- Slider
- Spatial Menu (WIP placeholder)
- Tabs
- Toaster
- Toggle
- Tooltip
- Tree

## Getting started

```bash
npm install
npm run dev -- --open
```

> **Note:** Package installation requires access to the public npm registry. If you are working in an
> offline environment, mirror the dependencies (including Svelte 5 and `@melt-ui/svelte` ≥ 0.91) before
> running `npm install`.

## Project structure

```
src/
├─ routes/
│  ├─ +layout.svelte      # Shared layout with a navigation bar
│  ├─ +page.svelte        # Home page introduction
│  └─ melt-components/
│     └─ +page.svelte     # Component gallery powered by Melt UI primitives
└─ app.html               # Document template used by SvelteKit
```

Feel free to extend any example, swap the styling, or integrate additional Melt UI primitives.
