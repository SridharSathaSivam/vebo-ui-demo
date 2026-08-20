# React demo

This example shows the intended React adapter contract for Vebo native Web Components.

```tsx
import { useState } from 'react';
import { VeboDateRangePicker } from '@vebo/react';

export default function App() {
  const [value, setValue] = useState<[string, string]>(['2026-08-20', '2026-08-25']);

  return (
    <VeboDateRangePicker
      value={value}
      onVeboChange={(event) => setValue(event.detail.value)}
    />
  );
}
```

The wrapper uses a ref to the native element and maps `CustomEvent` to a React callback.
