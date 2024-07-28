## Explained
- Used for choosing a provider token for non-class dependencies such as interfaces, [[String Token]] and objects.
- This means we can depend on strings, such as “Hello world!”, and objects, which include configuration objects and global variables such as Web APIs.
- InjectionToken ensures that the tokens are always unique. Even if the two libraries use the same name for the Angular Dependency Injection System, inject the right dependency.

## Purpose
#### Interfaces
- A TypeScript interface does not have a runtime representation.
- Because there is no interface for Angular to find at runtime, the interface cannot be a token, nor can you inject it:

```typescript
// Can't use interface as provider token
[{ provide: AppConfig, useValue: HERO_DI_CONFIG })]
```

```typescript
// Can't inject using the interface as the parameter type
constructor(private config: AppConfig){ }
```

- The above example tries to use the built-in `AppConfig` interface defined by Angular but this will fail because an interface cannot be used as a DI token.

#### String Token
- See [[String Token#Problem With String Tokens]] for more details on why `InjectionToken` is useful for raw strings. 

## Examples
#### Interfaces
- AppConfig is the built in Angular interface that represents the information in the `app.config` file.
- We can't inject this directly as is but we can use an InjectionToken as a solution
- The following example defines a token, `APP_CONFIG` of the type `InjectionToken`.

```typescript
import { InjectionToken } from '@angular/core'; 
export const APP_CONFIG = new InjectionToken<AppConfig>('app.config');
```

- `'app.config'` just gives a description of the token to specify the token’s purpose (can be an empty string).
- Next, register the dependency provider in the component using the `InjectionToken` object of `APP_CONFIG`.

```typescript
providers: [{ provide: APP_CONFIG, useValue: HERO_DI_CONFIG }]
```

- Now, inject the configuration object into the constructor with `@Inject` parameter decorator:

```typescript
constructor(@Inject(APP_CONFIG) config: AppConfig) { 
	this.title = config.title; 
}
```

#### Other Examples
```typescript
import { InjectionToken } from '@angular/core';
import { ProductService } from './product.service';
 
//export const APIURL = new InjectionToken<string>('Api.url');
export const APIURL = new InjectionToken('');
export const USE_FAKE = new InjectionToken<boolean>('Fake');
export const PRODUCT_SERVICE = new InjectionToken<ProductService>(
  'Product.Service'
);
export const APP_CONFIG = new InjectionToken<any>('Application.Config');
```


## Use Cases
- Very good use case example [here](https://medium.com/ngconf/configure-your-angular-apps-with-an-injection-token-be16eee59c40)