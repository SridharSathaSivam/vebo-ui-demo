# Angular demo

The Angular adapter is designed around `ControlValueAccessor`, so Vebo form components participate in Reactive Forms naturally.

```ts
import { FormControl, FormGroup } from '@angular/forms';

form = new FormGroup({
  range: new FormControl<[string, string]>(['2026-08-20', '2026-08-25'])
});
```

```html
<form [formGroup]="form">
  <vebo-date-range-picker formControlName="range"></vebo-date-range-picker>
</form>
```

Changes from the native `veboChange` event are forwarded to Angular's registered `onChange` callback, while touched and disabled state are also supported.
