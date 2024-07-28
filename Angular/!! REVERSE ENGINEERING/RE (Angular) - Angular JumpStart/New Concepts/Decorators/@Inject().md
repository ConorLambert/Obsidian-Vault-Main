## Purpose
- Manual mechanism for letting Angular know that a parameter must be injected.
- This is not required for class name dependencies as they are valid DI tokens.
- Generally used in conjunction with [[InjectionToken]] for injecting dependencies that cannot be represented by a class name such as objects, interfaces or string tokens.


## Example: InjectionToken
```typescript
//// app.config.ts
import { InjectionToken } from '@angular/core';
export const APP_CONFIG = new InjectionToken<AppConfig>('app.config');

//// src/app/app.component.ts
constructor(@Inject(APP_CONFIG) config: AppConfig) 
{ 
	this.title = config.title; 
}
```
