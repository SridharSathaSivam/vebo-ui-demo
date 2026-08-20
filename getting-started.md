# Vebo UI — Getting Started

Vebo UI is a framework-agnostic Web Component library. Components are native Custom Elements, so the same Vebo component can be used from plain HTML, React, Vue, Angular and other frameworks.

## 1. Use the native Web Components

```html
<script type="module" src="./vebo-ui.js"></script>

<vebo-button variant="primary">Save</vebo-button>
<vebo-input type="email" placeholder="Email"></vebo-input>
<vebo-date-range-picker></vebo-date-range-picker>
```

## 2. React

Install React and the generated Vebo React adapter in an application, then register the native elements before rendering them.

```tsx
import { useState } from 'react';
import { VeboDateRangePicker } from '@vebo/react';

export function App() {
  const [range, setRange] = useState<[string, string]>(['', '']);

  return (
    <VeboDateRangePicker
      value={range}
      onVeboChange={(event) => setRange(event.detail.value)}
    />
  );
}
```

## 3. Vue 3

```vue
<script setup lang="ts">
import { ref } from 'vue';
import { VeboDateRangePicker } from '@vebo/vue';

const range = ref<[string, string]>(['', '']);
</script>

<template>
  <VeboDateRangePicker v-model="range" />
</template>
```

The wrapper maps the DOM `veboChange` event to Vue's `update:modelValue` contract.

## 4. Angular

Import the Vebo Angular adapter and use the generated ControlValueAccessor with Reactive Forms.

```ts
import { FormControl, FormGroup } from '@angular/forms';

form = new FormGroup({
  range: new FormControl<[string, string]>(['', ''])
});
```

```html
<form [formGroup]="form">
  <vebo-date-range-picker formControlName="range"></vebo-date-range-picker>
</form>
```

The adapter forwards `writeValue`, change, touched and disabled state to the native Vebo element.

## 5. Build from the Vebo compiler

The compiler accepts the Vebo decorator DSL and emits native Web Components plus framework adapters.

```text
TypeScript decorators
        ↓
TypeScript AST
        ↓
Vebo Component IR
        ↓
Native Custom Element
        ├── React adapter
        ├── Vue adapter
        ├── Angular adapter
        └── Svelte adapter
```

Vebo does not require Stencil at runtime. The browser supplies Custom Elements, Shadow DOM, HTML templates, CSS custom properties and CustomEvent.

## Events

DOM-native events use `CustomEvent` and expose their data through `event.detail`.

```ts
picker.addEventListener('veboChange', (event) => {
  const range = (event as CustomEvent<{ value: [string, string] }>).detail.value;
  console.log(range);
});
```

## Design tokens

Customize Vebo with CSS custom properties rather than changing component internals:

```css
:root {
  --vebo-color-primary: #0f6cbd;
  --vebo-radius-md: 4px;
  --vebo-space-md: 16px;
}
```
