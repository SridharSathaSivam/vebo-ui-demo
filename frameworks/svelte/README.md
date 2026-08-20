# Svelte demo

Vebo is a native Web Component, so Svelte can bind to its public properties and listen to its DOM events.

```svelte
<script lang="ts">
  let range: [string, string] = ['2026-08-20', '2026-08-25'];

  function handleChange(event: CustomEvent<{ value: [string, string] }>) {
    range = event.detail.value;
  }
</script>

<vebo-date-range-picker bind:value={range} on:veboChange={handleChange} />
```
