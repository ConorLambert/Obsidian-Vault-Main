- A provider object defines how to obtain an injectable dependency associated with a [[! Tokens|DI token]].
- A provider is an instruction that describes how an object for a certain [[! Tokens|token]] is created.
- An [[Injector]] uses the provider to create a new instance of a dependency for a class that requires it.
- Please note that providing your service does not instantiate it. A service is instantiated only when it is injected.

## Example

- We declare the `Provider` with `providers` metadata. This is what it looks like:
```typescript
providers :[{ provide: ProductService, useClass: ProductService }]
```
###### provide
- The first property `provide` holds the [[! Tokens|Token]] or DI Token. 
- The DI systems uses the token as a key when locating a provider in the `providers` array.