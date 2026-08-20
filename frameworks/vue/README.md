# Vue 3 demo

Use the generated Vue adapter with Vue 3's `v-model` contract.

```vue
<script setup lang="ts">
import { ref } from 'vue';
import { VeboDateRangePicker } from '@vebo/vue';

const range = ref<[string, string]>(['2026-08-20', '2026-08-25']);
</script>

<template>
  <VeboDateRangePicker v-model="range" />
</template>
```

The adapter maps `value` to the component property and `veboChange` to `update:modelValue`.
