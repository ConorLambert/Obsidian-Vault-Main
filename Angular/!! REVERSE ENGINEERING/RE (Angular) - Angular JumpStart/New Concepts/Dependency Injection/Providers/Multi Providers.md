### Explained
- Provide multiple dependencies for a single token
- Requesting a dependency for that token will result in a list of all registered and provided values.
- Used for pluggable hooks that can be extended from the outside world.
- We can extend the thing that is being injected for a particular token as opposed to overwriting it based on the "the last one wins" rule i.e. if two or more providers have the same token then the last one defined wins.
- `multi: true` prevents the provider from overwriting any previous provider with the same token. Note that the previous provider must also have `multi: true` set.

### Example

```typescript
import { Component, InjectionToken, Inject } from '@angular/core';

export const TOKEN = new InjectionToken<string>('MyToken');

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss'],
  providers: [
    { provide: TOKEN, useValue: 'my injected object 1', multi: true },
    { provide: TOKEN, useValue: 'my injected object 2', multi: true },
  ],
})
export class AppComponent {
  constructor(@Inject(TOKEN) public myInjectObject: string) {
    console.log(myInjectObject);
  }
}
```

- We now see both values, `my injected object 1` and `my injected object 2`, in the array in the console. 
- Remove `multi: true` from one of them, you get an error. 
- Remove it from both, you will get `my injected object 2` which is the value you provided last.

### Use Cases

###### Validators
- Angular provides built-in validators through the `NG_VALIDATORS` and `NG_ASYNC_VALIDATORS` interfaces.
- Because this functionality is setup using multi providers, developers can extend this functionality by adding there own validators.
- Developers adding their own validators will not overwrite the validators that Angular has already built in.
